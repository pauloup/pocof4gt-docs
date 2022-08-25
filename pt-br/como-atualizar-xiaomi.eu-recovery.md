# Como atualizar a Xiaomi.eu na Recovery
## Sobre
A Xiaomi.eu versão 13.0.11 lançada em 24/08/2022 é uma ROM Recovery, o q significa q é preciso usar o TWRP para instalação.

Esse tutorial é indicado se você está em uma versão anterior da Xiaomi.eu instalada por script no Fastboot, e quer atualizar para a 13.0.11 versão Recovery.

Se você está na MIUI stock e quer instalar a Xiaomi pela primeira vez, esse tutorial não tem todos os passos necessários e não é indicado.

## Você precisa
- Estar na Xiaomi.eu com Bootloader desbloqueado.
- Ter Depuração ADB ativa e fastboot funcionando corretamente no computador.
- Baixar a ROM da [Xiaomi.eu 13.0.11](https://sourceforge.net/projects/xiaomi-eu-multilang-miui-roms/files/xiaomi.eu/MIUI-STABLE-RELEASES/MIUIv13/xiaomi.eu_multi_INGRES_V13.0.11.0.SLJCNXM_v13-12.zip/download) no celular.
- Baixar o [TWRP pro ingres versão Boot](https://dl.akr-developers.com/?file=skkk/TWRP/A12/v5.6_A12/%5BBOOT%5D3.6.2_12-RedmiK50G_v5.6_A12-ingres-skkk_427a1bbc.zip) no computador.

## Passo a Passo
1. Reiniciar o celular no modo Fastboot. Um jeito é desligar e depois apertar os botões Ligar e Aumentar Volume ao mesmo tempo.
2. Conectar o celular ao computador pelo cabo USB e confirmar que ele foi reconhecido pelo ADB usando o comando: 
	```
	fastboot devices
    ```
3. Dar boot no TWRP sem intala-lo no celular usando o comando abaixo, trocando "twrp.img" pelo caminho correto. Você pode arrastar e soltar o arquivo do TWRP para a janela de comandos para colar o caminho.
    ```
    fastboot boot "twrp.img"
    ```
4. O TWRP vai iniciar, e você já pode desconectar o celular do computador, se preferir. Quando a inicialização terminar, digite a senha para descriptografar o sistema e confirme.
	![](imagens/guia-xiaomi.eu.recovery-passo04.jpg)
5. Toque em "Install" e selecione o arquivo da ROM no armazenamento interno.
	![](imagens/guia-xiaomi.eu.recovery-passo05.jpg)
6. Arraste a seta azul para iniciar a instalação.
	![](imagens/guia-xiaomi.eu.recovery-passo06.jpg)
7. (Final) Quando o processo terminar, toque em "Reboot System". O sistema vai iniciar e a instalação foi concluída com sucesso.
8. (Opcional) Se você tinha feito Root no sistema e/ou usou o KonaBess para modificar a GPU, é necessário refazer esses procedimentos. Depois disso, pode ser necessário corrigir apps que iniciam com o sistema e usam Root, como o Magisk (especialmente com a opção Hide, que muda o nome do pacote) ou o FKM. Para isso, desative e ative de novo a opção de "Inicio automático" na tela de Informações do app.



