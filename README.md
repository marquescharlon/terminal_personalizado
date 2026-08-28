# Terminal Personalizado no Windows

Guia rápido para configurar um terminal personalizado no Windows utilizando **Windows Terminal + PowerShell + Oh My Posh + Nerd Font**.

---

## 📑 Glossário

| Etapa                                                                       | Ação                                        |
| --------------------------------------------------------------------------- | ------------------------------------------- |
| [1. Instalar o Oh My Posh](#1-instalar-o-oh-my-posh)                        | Instalação pelo Winget                      |
| [2. Instalar uma Nerd Font](#2-instalar-uma-nerd-font)                      | Instalação da fonte Meslo                   |
| [3. Configurar a fonte](#3-configurar-a-fonte-no-windows-terminal)          | Selecionar a fonte no Windows Terminal      |
| [4. Criar o perfil do PowerShell](#4-criar-o-perfil-do-powershell)          | Criar o arquivo `$PROFILE`                  |
| [5. Abrir o perfil](#5-abrir-o-perfil)                                      | Editar o `$PROFILE`                         |
| [6. Ativar o Oh My Posh](#6-ativar-o-oh-my-posh)                            | Carregar o Oh My Posh automaticamente       |
| [7. Visualizar os temas](#7-visualizar-os-temas-disponíveis)                | Listar os temas disponíveis                 |
| [8. Configurar um tema](#8-configurar-um-tema)                              | Escolher o tema do terminal                 |
| [9. Atualizar o Oh My Posh](#9-atualizar-o-oh-my-posh)                      | Atualizar pelo Winget                       |
| [10. Resolver problemas com o perfil](#10-problemas-com-execução-do-perfil) | Corrigir bloqueio de execução do PowerShell |
| [11. Comandos úteis](#11-comandos-úteis)                                    | Consulta rápida de comandos                 |
| [12. Documentação](#12-documentação)                                        | Links oficiais                              |

---

## 1. Instalar o Oh My Posh

Abra o **PowerShell** no Windows Terminal e execute:

```powershell
winget install JanDeDobbeleer.OhMyPosh --source winget
```

Após a instalação, **feche e abra novamente o terminal**.

Confirme a instalação:

```powershell
oh-my-posh version
```

[⬆ Voltar ao Glossário](#-glossário)

---

## 2. Instalar uma Nerd Font

Os temas do Oh My Posh utilizam ícones especiais. Para exibi-los corretamente, instale uma **Nerd Font**.

A fonte recomendada é a **Meslo**:

```powershell
oh-my-posh font install meslo
```

Para visualizar outras fontes disponíveis:

```powershell
oh-my-posh font list
```

[⬆ Voltar ao Glossário](#-glossário)

---

## 3. Configurar a fonte no Windows Terminal

Abra:

**Windows Terminal → Configurações → Perfis → Padrões → Aparência**

Em **Tipo de fonte**, selecione:

```text
MesloLGM Nerd Font
```

Salve as alterações.

[⬆ Voltar ao Glossário](#-glossário)

---

## 4. Criar o perfil do PowerShell

Verifique se o arquivo de perfil existe:

```powershell
Test-Path $PROFILE
```

Se retornar:

```text
False
```

crie o arquivo:

```powershell
New-Item -Path $PROFILE -Type File -Force
```

[⬆ Voltar ao Glossário](#-glossário)

---

## 5. Abrir o perfil

Execute:

```powershell
notepad $PROFILE
```

O Bloco de Notas será aberto com o arquivo de configuração do PowerShell.

[⬆ Voltar ao Glossário](#-glossário)

---

## 6. Ativar o Oh My Posh

Adicione ao `$PROFILE`:

```powershell
oh-my-posh init pwsh | Invoke-Expression
```

Salve o arquivo.

Recarregue o perfil:

```powershell
. $PROFILE
```

O Oh My Posh deverá aparecer no terminal.

[⬆ Voltar ao Glossário](#-glossário)

---

## 7. Visualizar os temas disponíveis

Execute:

```powershell
oh-my-posh get themes
```

Escolha o tema desejado.

[⬆ Voltar ao Glossário](#-glossário)

---

## 8. Configurar um tema

Abra novamente o perfil:

```powershell
notepad $PROFILE
```

Configure o tema desejado:

```powershell
oh-my-posh init pwsh --config "NOME_DO_TEMA" | Invoke-Expression
```

Exemplo:

```powershell
oh-my-posh init pwsh --config "cloud-native-azure" | Invoke-Expression
```

Salve o arquivo e recarregue:

```powershell
. $PROFILE
```

[⬆ Voltar ao Glossário](#-glossário)

---

## 9. Atualizar o Oh My Posh

Execute:

```powershell
winget upgrade JanDeDobbeleer.OhMyPosh --source winget
```

Depois da atualização, feche e abra novamente o Windows Terminal.

[⬆ Voltar ao Glossário](#-glossário)

---

## 10. Problemas com execução do perfil

Verifique a política atual:

```powershell
Get-ExecutionPolicy
```

Se a execução de scripts estiver bloqueada:

```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```

Confirme a alteração quando solicitado.

Recarregue o perfil:

```powershell
. $PROFILE
```

[⬆ Voltar ao Glossário](#-glossário)

---

## 11. Comandos úteis

| Ação              | Comando                                                  |
| ----------------- | -------------------------------------------------------- |
| Ver versão        | `oh-my-posh version`                                     |
| Listar fontes     | `oh-my-posh font list`                                   |
| Listar temas      | `oh-my-posh get themes`                                  |
| Abrir perfil      | `notepad $PROFILE`                                       |
| Recarregar perfil | `. $PROFILE`                                             |
| Atualizar         | `winget upgrade JanDeDobbeleer.OhMyPosh --source winget` |

[⬆ Voltar ao Glossário](#-glossário)

---

## 12. Documentação

* [Oh My Posh](https://ohmyposh.dev/)
* [Instalação no Windows](https://ohmyposh.dev/docs/installation/windows)
* [Nerd Fonts](https://ohmyposh.dev/docs/installation/fonts)
* [Temas](https://ohmyposh.dev/docs/themes)

[⬆ Voltar ao Glossário](#-glossário)

---

## ✅ Configuração concluída

Após concluir as etapas, o Windows Terminal estará configurado com:

* **Oh My Posh** instalado;
* **Nerd Font** configurada;
* ícones compatíveis;
* tema personalizado;
* inicialização automática pelo PowerShell;
* atualização pelo Winget.

> **Dica:** use o [Glossário](#-glossário) no início deste README para navegar rapidamente entre as etapas.
