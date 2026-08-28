# 🖥️ Terminal Personalizado no Windows

<img width="1113" height="297" alt="image" src="https://github.com/user-attachments/assets/3dda974d-fd96-49c8-84b5-10476b186318" />


Guia rápido para instalar e configurar um terminal personalizado no Windows utilizando **Windows Terminal + PowerShell + Oh My Posh + Nerd Font**.

O objetivo deste guia é permitir que toda a configuração seja realizada de forma simples, seguindo as etapas na ordem apresentada.

---

## 📑 Índice

| Etapa                                                                        | Descrição                        |
| ---------------------------------------------------------------------------- | -------------------------------- |
| [1. Instalar o Oh My Posh](#1-instalar-o-oh-my-posh)                         | Instalação utilizando Winget     |
| [2. Instalar uma Nerd Font](#2-instalar-uma-nerd-font)                       | Instalação da fonte Meslo        |
| [3. Configurar a fonte](#3-configurar-a-fonte-no-windows-terminal)           | Configuração no Windows Terminal |
| [4. Criar o perfil do PowerShell](#4-criar-o-perfil-do-powershell)           | Criação do arquivo `$PROFILE`    |
| [5. Abrir o perfil](#5-abrir-o-perfil-do-powershell)                         | Edição do `$PROFILE`             |
| [6. Ativar o Oh My Posh](#6-ativar-o-oh-my-posh)                             | Inicialização automática         |
| [7. Visualizar os temas](#7-visualizar-os-temas-disponíveis)                 | Listagem dos temas instalados    |
| [8. Configurar um tema](#8-configurar-um-tema)                               | Personalização do terminal       |
| [9. Atualizar o Oh My Posh](#9-atualizar-o-oh-my-posh)                       | Atualização utilizando Winget    |
| [10. Problemas com execução do perfil](#10-problemas-com-execução-do-perfil) | Correção da política de execução |
| [11. Comandos úteis](#11-comandos-úteis)                                     | Consulta rápida                  |
| [12. Desinstalar completamente](#12-desinstalar-completamente-o-oh-my-posh)  | Remoção do Oh My Posh            |
| [13. Documentação](#13-documentação)                                         | Links oficiais                   |

---

# 1. Instalar o Oh My Posh

Abra o **PowerShell** no Windows Terminal e execute:

```powershell
winget install JanDeDobbeleer.OhMyPosh --source winget
```

Após concluir a instalação, **feche e abra novamente o Windows Terminal**.

Verifique se a instalação foi realizada corretamente:

```powershell
oh-my-posh version
```

Se a versão instalada for exibida, o Oh My Posh está funcionando.

[⬆ Voltar ao Índice](#-índice)

---

# 2. Instalar uma Nerd Font

Os temas do Oh My Posh utilizam caracteres e ícones especiais.

Para que sejam exibidos corretamente, é necessário utilizar uma **Nerd Font**.

Instale a fonte **Meslo**:

```powershell
oh-my-posh font install meslo
```

Para visualizar todas as fontes disponíveis:

```powershell
oh-my-posh font list
```

[⬆ Voltar ao Índice](#-índice)

---

# 3. Configurar a fonte no Windows Terminal

Após instalar a fonte, configure o Windows Terminal para utilizá-la.

Abra:

**Windows Terminal → Configurações → Perfis → Padrões → Aparência**

Localize:

**Tipo de fonte**

Selecione:

```text
MesloLGM Nerd Font
```

Salve as alterações.

> Caso a fonte não apareça imediatamente, feche e abra novamente o Windows Terminal.

[⬆ Voltar ao Índice](#-índice)

---

# 4. Criar o perfil do PowerShell

O Oh My Posh precisa ser carregado pelo perfil do PowerShell sempre que um novo terminal for aberto.

Verifique se o perfil já existe:

```powershell
Test-Path $PROFILE
```

Se retornar:

```text
True
```

o perfil já existe e você pode seguir para a próxima etapa.

Se retornar:

```text
False
```

crie o arquivo:

```powershell
New-Item -Path $PROFILE -Type File -Force
```

[⬆ Voltar ao Índice](#-índice)

---

# 5. Abrir o perfil do PowerShell

Abra o arquivo `$PROFILE`:

```powershell
notepad $PROFILE
```

O arquivo será aberto no Bloco de Notas.

É nele que ficará a configuração responsável por carregar automaticamente o Oh My Posh.

[⬆ Voltar ao Índice](#-índice)

---

# 6. Ativar o Oh My Posh

Dentro do arquivo `$PROFILE`, adicione:

```powershell
oh-my-posh init pwsh | Invoke-Expression
```

Salve e feche o arquivo.

Depois, recarregue o perfil:

```powershell
. $PROFILE
```

O Oh My Posh deverá ser carregado imediatamente.

Caso prefira, feche e abra novamente o Windows Terminal.

[⬆ Voltar ao Índice](#-índice)

---

# 7. Visualizar os temas disponíveis

O Oh My Posh possui diversos temas prontos.

Para visualizá-los, execute:

```powershell
oh-my-posh get themes
```

Escolha o tema que deseja utilizar.

[⬆ Voltar ao Índice](#-índice)

---

# 8. Configurar um tema

Abra novamente o perfil:

```powershell
notepad $PROFILE
```

Localize:

```powershell
oh-my-posh init pwsh | Invoke-Expression
```

Substitua pela configuração contendo o tema desejado:

```powershell
oh-my-posh init pwsh --config "NOME_DO_TEMA" | Invoke-Expression
Clear-Host
```

Por exemplo:

```powershell
oh-my-posh init pwsh --config "spaceship" | Invoke-Expression
Clear-Host
```

Salve o arquivo.

Depois, recarregue o perfil:

```powershell
. $PROFILE
```

Ou simplesmente feche e abra novamente o Windows Terminal.

[⬆ Voltar ao Índice](#-índice)

---

# 9. Atualizar o Oh My Posh

Para verificar e instalar atualizações utilizando o Winget:

```powershell
winget upgrade JanDeDobbeleer.OhMyPosh --source winget
```

Após a atualização, feche e abra novamente o Windows Terminal.

Para confirmar a versão instalada:

```powershell
oh-my-posh version
```

[⬆ Voltar ao Índice](#-índice)

---

# 10. Problemas com execução do perfil

Caso apareça uma mensagem informando que a execução de scripts está desabilitada, verifique a política atual:

```powershell
Get-ExecutionPolicy
```

Se necessário, permita a execução de scripts locais para o usuário atual:

```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```

Confirme a alteração quando solicitado.

Depois, recarregue o perfil:

```powershell
. $PROFILE
```

> A opção `CurrentUser` aplica a alteração somente ao usuário atual do Windows.

[⬆ Voltar ao Índice](#-índice)

---

# 11. Comandos úteis

| Ação                           | Comando                                                    |
| ------------------------------ | ---------------------------------------------------------- |
| Ver versão instalada           | `oh-my-posh version`                                       |
| Listar fontes                  | `oh-my-posh font list`                                     |
| Instalar Meslo Nerd Font       | `oh-my-posh font install meslo`                            |
| Listar temas                   | `oh-my-posh get themes`                                    |
| Abrir o perfil                 | `notepad $PROFILE`                                         |
| Verificar se o perfil existe   | `Test-Path $PROFILE`                                       |
| Recarregar o perfil            | `. $PROFILE`                                               |
| Verificar política de execução | `Get-ExecutionPolicy`                                      |
| Atualizar Oh My Posh           | `winget upgrade JanDeDobbeleer.OhMyPosh --source winget`   |
| Desinstalar Oh My Posh         | `winget uninstall JanDeDobbeleer.OhMyPosh --source winget` |

[⬆ Voltar ao Índice](#-índice)

---

# 12. Desinstalar completamente o Oh My Posh

Caso queira remover o Oh My Posh, siga as etapas abaixo.

## 12.1 Desinstalar pelo Winget

Execute:

```powershell
winget uninstall JanDeDobbeleer.OhMyPosh --source winget
```

---

## 12.2 Remover a configuração do PowerShell

A desinstalação pelo Winget **não remove automaticamente a configuração existente no `$PROFILE`**.

Abra o perfil:

```powershell
notepad $PROFILE
```

Localize e remova a linha:

```powershell
oh-my-posh init pwsh | Invoke-Expression
```

Caso esteja utilizando um tema personalizado, remova a linha semelhante a:

```powershell
oh-my-posh init pwsh --config "NOME_DO_TEMA" | Invoke-Expression
```

Salve o arquivo.

---

## 12.3 Reiniciar o terminal

Feche todas as janelas do Windows Terminal.

Abra novamente o terminal.

Verifique se o comando ainda está disponível:

```powershell
oh-my-posh version
```

Caso o Oh My Posh tenha sido removido corretamente, o comando não deverá mais ser reconhecido.

> A Nerd Font instalada pode permanecer no Windows, pois ela pode ser utilizada por outros programas. Sua remoção é opcional.

[⬆ Voltar ao Índice](#-índice)

---

# 13. Documentação

Para informações adicionais ou mudanças futuras no processo de instalação, consulte a documentação oficial:

* [Oh My Posh](https://ohmyposh.dev/)
* [Instalação no Windows](https://ohmyposh.dev/docs/installation/windows)
* [Configuração](https://ohmyposh.dev/docs/installation/customize)
* [Nerd Fonts](https://ohmyposh.dev/docs/installation/fonts)
* [Temas](https://ohmyposh.dev/docs/themes)

[⬆ Voltar ao Índice](#-índice)

---

# ✅ Configuração concluída

Após concluir este guia, seu Windows Terminal estará configurado com:

* **Oh My Posh** instalado pelo Winget;
* **Meslo Nerd Font**;
* suporte aos ícones dos temas;
* perfil do PowerShell configurado;
* inicialização automática do Oh My Posh;
* tema personalizado;
* atualização pelo Winget.

---

## 🔄 Instalação rápida

Para uma nova instalação, a sequência principal é:

```powershell
winget install JanDeDobbeleer.OhMyPosh --source winget
```

```powershell
oh-my-posh font install meslo
```

```powershell
New-Item -Path $PROFILE -Type File -Force
```

```powershell
notepad $PROFILE
```

Adicione ao `$PROFILE`:

```powershell
oh-my-posh init pwsh | Invoke-Expression
```

Recarregue:

```powershell
. $PROFILE
```

Pronto. O **Oh My Posh** estará configurado para ser carregado automaticamente sempre que o PowerShell for iniciado.
