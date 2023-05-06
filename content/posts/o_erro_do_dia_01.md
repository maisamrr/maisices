---
date: "2023-02-18"
tags: ["fail", "Linux"]
title: "O erro do dia - boot no sistema operacional"
toc: true
---

Um simples boot de sistema operacional que durou horas *rs rs rs*

Fui instalar o Ubuntu num notebook antigo que eu tinha aqui. Tinha tudo pra ser fácil, criei um USB bootável com a ISO, entrei no modo BIOS e ajeitei pra o USB ser prioridade, beleza. Fiz toda a instalação bonitinha e quando tive que dar o reset na máquina, ele ficava inicializando e dando erro, pedindo o pendrive. Entrei no modo BIOS de novo e setei a prioridade do drive pra não ser mais o USD. Deu em nada. #fail

Tentei reinstalar o Ubuntu, beleza. Mesmo erro todo de novo. Desisti e pensei, poxa, já instalei o Pop OS antes, vamos tentar e ver se não é mais fácil… Foi mais fácil, só fiz o pendrive bootável com a ISO da versão 22.04 e inseri na máquina, ao ligar já inicializou a instalação que concluí com sucesso.

Novo problema: quando eu fui usar o novo sistema operacional, simplesmente a janela de *Settings* não abria de jeito nenhum. Aparecia no ícone que tinha sido inicializada, mas nada da janela aparecer, inclusive com o *alt+tab* aparecia o programa pra alternar a janela, mas não abria ~~a porcaria das~~ Settings.

Rodei, rodei, fiz mil coisas que estavam por aí nos fóruns da vida, mas depois de hooooras a única coisa que funcionou foi fazer a atualização dos drivers.

```
sudo ubuntu-drivers autoinstall
```

E em seguida reiniciando o computador. Talvez fosse algo simples que eu deveria ter pensado no começo? Mas é isso aí. Um problema a menos na vida. Seguimos para o próximo problema, com a esperança de gastar menos horas.

[Link que me ajudou](https://askubuntu.com/questions/1281839/settings-window-doesnt-show-up-on-ubuntu-20-04-1-lts).

