---
title: Comandos devinit
description: Detalhes sobre como usar comandos devinit para instalar componentes.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 153864a293ca25fdcf30f23b96f686737411c965
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435782"
---
# <a name="devinit-commands"></a>comandos devinit

## <a name="init"></a>Init

```console
devinit init
```

Inicialize o ambiente executando as ferramentas especificadas em um [.devinit.jsno](devinit-json.md) arquivo.

### <a name="options-for-init"></a>Opções para init

Opções opcionais para o `devinit init` comando.

| Argumento             | Obrigatório | Descrição                                                               |
|----------------------|----------|---------------------------------------------------------------------------|
| -f,--file            | No       | Caminho para o `.devinit.json` arquivo.                                         |
| --ação de erro       | No       | Especifica como tratar erros. Opções: parar, ignorar, continuar (padrão).|
| -v,--detalhado         | No       | Emitir saída detalhada.                                                      |
| -n,--execução seca         | No       | Simulação de execução.                                                                  |

#### <a name="--file-argument"></a>--argumento de arquivo

Especifica o caminho para o _devinit.jsno_ arquivo. Se--file não for especificado, Pesquisaremos um arquivo padrão nos seguintes locais:

* {diretório atual} \\.devinit.jsem
* {diretório atual} \\devinit.jsem
* {diretório atual} \\ . devinit \\.devinit.jsem
* {diretório atual} \\ . devinit \\devinit.jsem
* {diretório atual} \\ devinit \\.devinit.jsem
* {diretório atual} \\ devinit \\devinit.jsem
* {diretório atual} \\ . devcontainer \\.devinit.jsem
* {diretório atual} \\ . devcontainer \\devinit.jsem

> [!NOTE]
> Se vários arquivos padrão forem encontrados, o devinit usará o arquivo que aparece primeiro na lista acima.

#### <a name="--error-action-argument"></a>--argumento de ação de erro

Veja [abaixo](#options-for-run).

#### <a name="--verbose-switch"></a>--opção detalhada

Veja [abaixo](#options-for-run).

#### <a name="--dry-run-switch"></a>--opção de execução seca

Veja [abaixo](#options-for-run).

## <a name="run"></a>Executar

```console
devinit run -t <toolname>
```

Executa a ferramenta específica, os parâmetros são listados abaixo. Consulte a [documentação](devinit-tool-list.md) para cada ferramenta para uso específico.

### <a name="options-for-run"></a>Opções de execução

Opções para o `devinit run` comando.

| Argumento                                      | Obrigatório | Descrição                                                                          |
|-----------------------------------------------|----------|--------------------------------------------------------------------------------------|
| -t,--ferramenta                                     | Yes      | Obrigatórios. O nome da ferramenta.                                                             |
| -i,--entrada                                    | No       | O valor de entrada da ferramenta. Por exemplo, um FileName, um pacote ou um nome.                     |
| --ação de erro                                | No       | Especifica como tratar erros de ferramenta: parar, ignorar, continuar. O padrão é parar. |
| -v,--detalhado                                  | No       | Emitir saída detalhada.                                                                 |
| -n,--execução seca                                  | No       | Simulação de execução.                                                                             |
| --&lt;arg1 &gt; &lt; arg2 &gt; ... &lt; argN&gt;  | No       | Argumentos de linha de comando adicionais para a ferramenta.                                       |

#### <a name="--error-action-argument"></a>--argumento de ação de erro

Especifica a ação a ser tomada se uma ferramenta retornar um código de saída diferente de zero. Os valores válidos são:

| Argumento | Descrição                                                                                                                                                                                                                                                                           |
|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| continue | Continue processando outras ferramentas depois de emitir um erro para o erro padrão. O código de saída devinit.exe é diferente de zero (falha). Esse comportamento é semelhante à ação de erro de parada, mas o processamento é continuado. `continue` é a ação de erro padrão para o comando init.              |
| ignore   | Continue processando outras ferramentas depois de emitir um aviso para a saída padrão. O código de saída do processo DevInit sempre deve ser zero (êxito). A `ignore` configuração ignora todos os erros.                                                                                                      |
| parar     | Emite um erro para o erro padrão e para as ferramentas de processamento. O código de saída devinit.exe é diferente de zero (falha). Isso é semelhante à ação de erro de continuação, mas o processamento é interrompido no primeiro erro encontrado. `stop` é a ação de erro padrão para todos os comandos, exceto init. |

#### <a name="--dry-run-switch"></a>--opção de execução seca

Comandos da ferramenta Echo que seriam executados. Algumas ferramentas podem executar mais ações, conforme documentado para essa ferramenta. 

#### <a name="--verbose-switch"></a>--opção detalhada

Emitir saída detalhada para a saída padrão. Se a ferramenta a ser executada oferecer suporte a uma opção detalhada, propague o comutador detalhado para a ferramenta.

#### <a name="--dry-run-switch"></a>--opção de execução seca

Comandos da ferramenta Echo que seriam executados, mas não executam nenhuma ferramenta.

#### <a name="additional-command-line-arguments"></a>Argumentos de linha de comando adicionais

Usar um `<arg>` que inclui um espaço em seu valor deve incluir um par adicional de aspas de escape.

```console
devinit run -t <toolname> -<somearg> "<some value>"
```

Para instalar o dotnet em um diretório específico `C:\Program Files\dotnet` :

```console
devinit run -t require-dotnetcoresdk --"-InstallDir \"C:\Program Files\dotnet\""
```

## <a name="list"></a>Lista

```console
devinit list
```

Imprime uma lista de todas as ferramentas disponíveis.

## <a name="show"></a>Mostrar

```console
devinit show -t <toolname>
```

| Argumento       | Obrigatório | Descrição                                                                          |
|----------------|----------|--------------------------------------------------------------------------------------|
| -t,--ferramenta      | Yes      | Obrigatórios. O nome da ferramenta.                                                             |

Imprime informações de ajuda para uma determinada ferramenta.

## <a name="version"></a>Versão

```console
devinit version
```

Imprime as informações de versão atuais para devinit.

## <a name="help"></a>Ajuda

```console
devinit help
devinit help list
```

Imprime o texto de ajuda para devinit ou para um comando específico `devinit <command>` .
 
