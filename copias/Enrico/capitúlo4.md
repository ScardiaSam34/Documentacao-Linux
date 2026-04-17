## Capitúlo 04.  Noções básicas de Linux e inicialização do sistema.
 Neste capitúlo vemos o que é necessário para a instalação do Linux em sua maquina, como partições e armazenamento, com base na distro da preferencia do usuario, no meu caso a escolhida foi o Ubuntu.
 Também vemos que o processo moderno de inicialização segue este fluxo: 
 Firmware (BIOS/UEFI): Realiza o POST e localiza o setor de boot.
 Bootloader (GRUB2): Carrega o Kernel e o initramfs (sistema de arquivos temporário na RAM).
 Kernel: Detecta o hardware e monta a raiz (/).
 Systemd (PID 1): O "pai" de todos os processos que gerencia serviços (units), substituindo o antigo SysVinit.
