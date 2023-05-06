---
date: "2023-05-06"
tags: ["computação gráfica", "faculdade"]
title: "Computação gráfica - Lista de exercícios 1"
toc: true
---

## Lista 1 - Computação gráfica
Engenharia e Ciência da Computação  
Prof. Thiago Raposo  
Maio/2023  

**01. Considere uma imagem 𝑓(𝑥,𝑦) com amplitude representada em valores reais no intervalo [0,1]. Considere, agora, uma imagem 𝑔(𝑥,𝑦) obtida a partir de 𝑓(𝑥,𝑦) pela relação 𝑔(𝑥, 𝑦) = [𝑓(𝑥, 𝑦)]ˆ𝛼. Qual o efeito, em termos qualitativos, resultante se 𝛼 > 1? E se 0 < 𝛼 < 1?**  
Sabendo que o gamma é o valor relativo à luminância, ou seja, as propriedades de tons claros e escuros da imagem, quando seu valor for 𝛼 > 1, a imagem resultante 𝑔(𝑥, 𝑦) irá escurecer, já que há um aumento na amplitude dos valores de intensidade em relação à imagem original. Isso resulta numa imagem com menor brilho.  
Já para valores 0 < 𝛼 < 1, a imagem irá clarear, pois há diminuição da diferença entre os valores de intensidade da imagem, reduzindo o contraste da imagem, apresentando assim uma imagem resultante com maior brilho.

**02. Considere que uma imagem X qualquer seja recebida por um algoritmo em MATLAB/Octave e que este realize o seguinte procedimento, fornecendo uma imagem Y como imagem de saída:**  
{{< highlight matlab >}}
function Y = algoritmo1(X)
[L,C] = size(X);
    for i = 1:L
        for j = 1:C
            Y(i,j) = (X(i,j))^2;  
        end   
    end  
{{< /highlight >}}
**Explique qual o efeito esperado deste procedimento, quando aplicado a uma imagem em escala de cinza, representada por reais no intervalo entre 0 e 1.**  
Como a imagem é representada por uma matriz de pixels em que cada pixel armazena um valor de intensidade entre 0 e 1, em que 0 representa preto absoluto e 1 representa branco absoluto, o procedimento acima eleva ao quadrado o valor contido em cada pixel da matriz.  
Assim, por exemplo, um valor 0.3 passaria a ser 0.09, distanciando esse valor do branco (valor 1). No geral, o efeito é uma imagem com menor brilho, pois ela irá escurecer com seus pixels distanciando-se mais de o valor 1 (branco).

**03. Considere o algoritmo em MATLAB a seguir, que gera uma imagem X.**
{{< highlight matlab >}}
function X = algoritmo
	X = zeros(1000,1000);
  for i = 101:900
	  for j = 101:900
			X(i,j) = 1;
		end 
	end
{{< /highlight >}}  
**Explique qual a forma da imagem X assim gerada e por quê. Faça um desenho desta imagem.**  
O algoritmo define inicialmente uma imagem de tamanho 1000x1000 preenchida de zeros, ou seja, toda preta. Em seguida, percorre das linhas 101 a 900 e das colunas 101 a 900, atribuindo o valor 1 a esses pixels, ou seja, tornando-os brancos.  
O que acontece é que todos os pixels atribuídos valor 1 formarão um quadrado branco de 800x800 pixels cercado por uma borda preta, dos pixels que não foram percorridos.

**04. Escreva, na linguagem MATLAB/Octave, um algoritmo que crie uma imagem binária e quadrada, de forma que, em seu canto superior esquerdo, contenha um quarto de um círculo centrado no vértice superior esquerdo. O quarto de círculo – incluindo-se seu interior – deve ser preto e o restante da imagem deve ser branco. O raio deste quarto de círculo deve ser igual a 1/3 do lado da imagem (arredondando para baixo, em caso de número fracionário), conforme ilustrado a seguir:** 

![Imagem quadrada com um quarto de círculo](img_04.png)

**Seu algoritmo deve, necessariamente:**
- **Receber exatamente 1 (um) parâmetro de entrada, que será o tamanho L da
imagem (lado do quadrado)**
- **Fornecer exatamente 1 (um) parâmetro de saída, que será uma matriz X
contendo a imagem construída.**

Resposta:  
{{< highlight matlab >}}
function[img] = circle(n)
X = ones(n,n);
circle_size = round(n/3);
 for i = 1:circle_size
	  for j = 1:circle_size
			%Verifica se o ponto (i,j) está dentro de um círculo centrado no ponto
			%(n/2, n/2) com raio igual a circle_size, calculando a distância entre o 
			%ponto (i,j) e o ponto central (n/2, n/2) usando a equação:
      if ((i - round(n/2))^2 + (j - round(n/2))^2) <= circle_size^2
        X(i,j) = 0;
      end
    end
 end
imshow(X);
{{< /highlight >}}

**06. Idem à questão anterior, para uma imagem contendo um losango em seu centro.**
Resposta:  
{{< highlight matlab >}}
function[img] = diamond(n)
X = zeros(n,n);
diamond_diagonal = n/2;
side = diamond_diagonal/sqrt(2);
xcenter = n/2;
ycenter = n/2;

vertexes = [xcenter+side, ycenter;  % vértice direito
xcenter, ycenter+side;  % vértice superior
xcenter-side, ycenter;  % vértice esquerdo
xcenter, ycenter-side]; % vértice inferior

for i = 1:n
	for j = 1:n
		%verifica se o ponto (i,j) está dentro do diamante
		%calcula a distância do ponto ao centro do diamante, somando a distância horizontal e a distância vertical
		%se essa soma for <= ao comprimento de cada lado do diamante, o ponto está dentro
		if (abs(i-xcenter) + abs(j-ycenter) <= side)
			X(i,j) = 1;
    end
  end
end
imshow(X);
end
{{< /highlight >}}
