# Terminal Personalizado

Com o "Oh My Posh" é possível deixar personalizado o seu prompt de comando, também conhecido como terminal. Abaixo um exemplo:

![image](https://github.com/user-attachments/assets/79b8ab65-ce0b-4aa4-9f0e-1c93ffb9c5cc)

Documentação:
- [Windows](https://ohmyposh.dev/docs/installation/windows)
- [Linux](https://ohmyposh.dev/docs/installation/linux)
- [MacOS](https://ohmyposh.dev/docs/installation/macos)

Para ter segurança de que todos os ícones sejam apresentados é recomendável utilizar a Nerd Font na hora de escolher o modelo da fonte.
Seguiremos a instalação para o Windows utilizando o seu gerenciador de pacotes, Winget.

# Instalação

1. Para realizar a instalação do Oh My Posh no Windows 10/11 através do Winget basta utilizar o comando abaixo:

```

winget install JanDeDobbeleer.OhMyPosh -s winget

```

Após executar o comando e finalizar a instalação feche e abra novamente o terminal. 

## Instalação da Fonte
- [Documentação](https://ohmyposh.dev/docs/installation/fonts)
- [Modelo de Fonte](https://www.nerdfonts.com/)

Esteja atento na hora de realizar a instalalação da fonte, por via das dúvidas utilize a HACK. 
Para instalação da fonte executar o comando abaixo:


```

oh-my-posh font install --user

```

![image](https://github.com/user-attachments/assets/7f33f261-12ce-4fee-bc7b-61162e45a39c)

![image](https://github.com/user-attachments/assets/7c7329bf-a4c6-4dea-997a-bf30ef129446)


_Ao executar o terminal como administrar a font será instalada no sistema, caso contrário, será instalada apenas no usuário local._

## Configuração da Fonte

Windows 10: 
- Clicar com botão direito do mouse na barra de título
- Clicar com o botão esquerdo na opção ``Propriedades``
- Navegar até a guia ``Fonte``
- Escolher a fonte ``Hack Nerd Font Mono``

Windows 11: 
- Clicar com botão direito do mouse na barra de título
- Clicar com o botão esquerdo na opção ``Configurações``
- Navegar até o menu ``Windows PowerShell``
- Clicar em ``Aparência``
- Então, em Tipo de fonte escolher a ``Hack Nerd Font``

## Alteração do Prompt do Shell

[Documentação](https://ohmyposh.dev/docs/installation/prompt)

a. Execute o comando abaixo para confirmar qual o Shell está em uso.

```

oh-my-posh get shell

```

b. Edite seu script de perfil do PowerShell. Por exemplo, usando o bloco de notas, para isso, basta acessar o terminal e digitar o comando ``notas:$PROFILE``.

c. Quando der erro informando que o perfil não existe certifique de clicar em ``Sim``, que deseja criá-lo. Se for o caso, tente o comando abaixo:

```

New-Item -Path $PROFILE -Type File -Force

```

> Nesse cenário, também pode ser que o PowerShell bloqueie a execução de scripts locais. Para resolver isso, defina o PowerShell para exigir apenas que scripts remotos sejam assinados usando o , ou assinar o perfil. ``Set-ExecutionPolicy RemoteSigned``

d. Em seguida, adicione a seguinte linha.

```

oh-my-posh init pwsh | Invoke-Expression
Clear-Host

```

e. Depois de adicionado o texo ao arquivo, recarregue seu perfil para que as alterações sejam aplicadas. Para isso, abra o PowerShell e execute o comando abaixo:

```

. $PROFILE

```

## Configuração do tema

Executar no PowerShwll os comandos abaixo:

```

Install-Module posh-git -Scope CurrentUser
Install-Module oh-my-posh -Scope CurrentUser

```

Para editar o seu $PROFILE execute o comando abaixo no PowerShell:

```

if (!(Test-Path -Path $PROFILE )) { New-Item -Type File -Path $PROFILE -Force }
notepad $PROFILE

```

Adicionar no arquivo a linha abaixo:

```

oh-my-posh init pwsh --config 'C:\Users\Usuario\AppData\Local\Programs\oh-my-posh\themes\cloud-native-azure.omp.json' | Invoke-Expression

```

> Verifica se a localização dos temas realmente estão no endereço neste exemplo, se estiver, só executar o comando acima.

Executar o comando abaixo para listar todos os temas disponíveis ou você pode consultar no site: https://ohmyposh.dev/docs/themes

```

Get-PoshThemes

```


