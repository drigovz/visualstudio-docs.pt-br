---
title: Comandos devinit
description: Detalhes sobre como usar comandos devinit para instalar componentes.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 545f7ec80b528b759db8ccfde21a18a46959913a
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809703"
---
# <a name="devinit-commands"></a>comandos devinit

## <a name="init"></a>Init

```batch
> devinit init
```

Inicialize o ambiente executando as ferramentas especificadas em um [_.devinit.jsno_](devinit-json.md) arquivo no diretório de trabalho atual.  

### <a name="options-for-init"></a>Opções para init

Opções opcionais para o `devinit init` comando.

| Argumento             | Obrigatório | Descrição                                                               |
|----------------------|----------|---------------------------------------------------------------------------|
| -f,--file           | Não       | Caminho para o _.devinit.jsno_ arquivo.                                         |
| --ação de erro       | Não       | Especifica como tratar erros. Opções: parar, ignorar, continuar (padrão).|
| -v,--detalhado         | Não       | Emitir saída detalhada.                                                      |
| -n,--execução seca         | Não       | Simulação de execução.                                                                  |

## <a name="run"></a>Executar

```batch
> devinit run -t <toolname>
```

Executa a ferramenta específica, os parâmetros são listados abaixo. Consulte a [documentação](devinit-tool-list.md) para cada ferramenta para uso específico.

### <a name="options-for-run"></a>Opções de execução

Opções para o `devinit run` comando.

| Argumento                                  | Obrigatório | Descrição                                                                          |
|-------------------------------------------|----------|--------------------------------------------------------------------------------------|
| -t,--ferramenta                                 | Sim      | Obrigatórios. O nome da ferramenta.                                                             |
| -i,--entrada                                | Não       | O valor de entrada da ferramenta. Por exemplo, um FileName, um pacote ou um nome.                           |
| --ação de erro                            | Não       | Especifica como tratar erros de ferramenta: parar, ignorar, continuar. O padrão é parar. |
| -v,--detalhado                              | Não       | Emitir saída detalhada.                                                                 |
| -n,--execução seca                              | Não       | Simulação de execução.                                                                             |
| --&lt;arg1 &gt; &lt; arg2 &gt; &lt; argN&gt;  | Não       | Argumentos de linha de comando adicionais para a ferramenta.                                       |

#### <a name="--file-argument"></a>--argumento de arquivo

Especifica o caminho para o _devinit.jsno arquivo. Se – file não for especificado, Pesquisaremos um arquivo padrão nos seguintes locais:

* {diretório atual} \\.devinit.jsem
* {diretório atual} \\ . devinit \\.devinit.jsem

Observação: caminhos sem a entrelinha `.` no diretório ou nome de arquivo também serão correspondentes.

#### <a name="--error-action-argument"></a>--argumento de ação de erro

Especifica a ação a ser tomada se uma ferramenta retornar um código de saída diferente de zero. Os valores válidos são:

| Argumento | Descrição                                                                                                                                                                                                                                                                           |
|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| continue | Continue processando outras ferramentas depois de emitir um erro para o erro padrão. O código de saída devinit.exe é diferente de zero (falha). Esse comportamento é semelhante à ação de erro de parada, mas o processamento é continuado. `continue` é a ação de erro padrão para o comando init.              |
| ignore   | Continue processando outras ferramentas depois de emitir um aviso para a saída padrão. O código de saída do processo DevInit sempre deve ser zero (êxito). A `ignore` configuração ignora todos os erros.                                                                                                      |
| parar     | Emite um erro para o erro padrão e para as ferramentas de processamento. O código de saída devinit.exe é diferente de zero (falha). Isso é semelhante à ação de erro de continuação, mas o processamento é interrompido no primeiro erro encontrado. `stop` é a ação de erro padrão para todos os comandos, exceto init. |

#### <a name="--dry-run-switch"></a>--opção de execução seca

Comandos da ferramenta Echo que seriam executados, mas não executam nenhuma ferramenta. 

#### <a name="--verbose-switch"></a>--opção detalhada

Emitir saída detalhada para a saída padrão. Se a ferramenta a ser executada oferecer suporte a uma opção detalhada, propague o comutador detalhado para a ferramenta.

#### <a name="note-on-additional-command-line-arguments"></a>Observação sobre argumentos de linha de comando adicionais

Usar um `<arg>` que inclui um espaço em seu valor deve incluir um par adicional de aspas de escape.

```batch
> devinit run -t <toolname> -<somearg> "<some value>"
```

Para instalar o dotnet em um diretório específico `C:\Program Files\dotnet` :

```batch
> devinit run -t require-dotnetcoresdk --"-InstallDir \"C:\Program Files\dotnet\""
```

## <a name="list"></a>Lista

```batch
> devinit list
```

Imprime uma lista de todas as ferramentas disponíveis.

## <a name="show"></a>Mostrar

```batch
> devinit show -t <toolname>
```

| Argumento       | Obrigatório | Descrição                                                                          |
|----------------|----------|--------------------------------------------------------------------------------------|
| -t,--ferramenta      | Sim      | Obrigatórios. O nome da ferramenta.                                                             |

Imprime informações de ajuda para uma determinada ferramenta.

## <a name="version"></a>Versão

```batch
> devinit version
```

Imprime as informações de versão atuais para devinit.

## <a name="help"></a>Ajuda

```batch
> devinit help
> devinit help list
```

Imprime o texto de ajuda para devinit ou para um comando específico `devinit <command>` .
 