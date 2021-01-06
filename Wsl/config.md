# Configuração do ambiente dev no WSL

## Configuração inicial

```
https://docs.microsoft.com/en-gb/windows/wsl/install-win10#step-4---download-the-linux-kernel-update-package
```
Baixe a distribuição na loja do windows e sigas os passos abaixo

## Abra windows + R e digite %userprofile% e enter

## Colocar .wslconfig na raiz
```
[wsl2]
KernelCommandLine = vsyscall=emulate
memory=4GB # Limits VM memory in WSL 2 to 4 GB
processors=5 # Makes the WSL 2 VM use two virtual processors
```

## Atualizações
```
sudo apt update
sudo apt upgrade
```

## Instalar php
```
sudo apt install php7.4
php --version
```

## Instalar composer
```
https://getcomposer.org/download/
```

## Configurar Path composer
Rode esse para funcionar o comando composer
```
export PATH="$PATH:$HOME/.composer/vendor/bin"
```

Se nao funcionar rode esse
```
sudo mv composer.phar /usr/bin/composer
```

se não funcionar rode esse 
```
export PATH="~/.config/composer/vendor/bin:$PATH"
```

## Instalando node + npm
```
sudo apt install nodejs
sudo apt install npm
```

## Instalar yarn
```
https://www.hostinger.com.br/tutoriais/yarn-install/
```

## Colocar Ubuntu como padrão
Abra o powershell e rode o comando
```
wslconfig /s Ubuntu-20.04
```
