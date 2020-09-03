---
title: Como caminhos de pesquisa de Python são aplicados
description: O Visual Studio fornece um meio mais específico para especificar caminhos de pesquisa para ambientes e projetos para evitar o uso de variáveis em todo o sistema.
ms.date: 03/13/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 10430c6eba57c97dd46a706d0ec2f532cd08d4f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88801159"
---
# <a name="how-visual-studio-uses-python-search-paths"></a>Como o Visual Studio usa caminhos de pesquisa de Python

Com o uso típico do Python, a variável de ambiente `PYTHONPATH` (ou `IRONPYTHONPATH`, etc.) fornece o caminho de pesquisa padrão para arquivos de módulo. Ou seja, quando você usa uma instrução `from <name> import...` ou `import <name>`, o Python pesquisa os seguintes locais, nessa ordem, por um nome correspondente:

1. Módulos internos do Python.
1. A pasta que contém o código do Python que você está executando.
1. O "caminho de pesquisa do módulo", conforme definido pela variável de ambiente aplicável. (Consulte [O caminho de pesquisa do módulo](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) e [Variáveis de ambiente](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) na documentação básica do Python.)

No entanto, o Visual Studio ignora a variável de ambiente do caminho de pesquisa, mesmo quando ela tiver sido configurada para todo o sistema. Ele é ignorado, de fato, precisamente *porque* está definido para todo o sistema e, portanto, gera determinadas perguntas que não podem ser respondidas automaticamente: os módulos referenciados destinam-se ao Python 2,7 ou Python 3.6 +? Eles substituirão os módulos da biblioteca padrão? O desenvolvedor está ciente desse comportamento ou essa é uma tentativa de sequestro mal-intencionada?

Dessa forma, o Visual Studio fornece um meio para especificar caminhos de pesquisa diretamente nos projetos e ambientes. O código que você executa ou depura no Visual Studio recebe os caminhos de pesquisa no valor de `PYTHONPATH` (e outras variáveis equivalentes). Ao adicionar caminhos de pesquisa, o Visual Studio inspeciona as bibliotecas nessas localizações e compila bancos de dados do IntelliSense para elas quando necessário (Visual Studio 2017 versão 15.5 e anterior; a criação do banco de dados pode demorar algum tempo, dependendo do número de bibliotecas).

Para adicionar um caminho de pesquisa, vá para **Gerenciador de soluções**, expanda o nó do projeto, clique com o botão direito do mouse em **caminhos de pesquisa**e selecione **Adicionar pasta ao caminho de pesquisa**:

::: moniker range="vs-2017"
![Comando Adicionar Pasta ao Caminho de Pesquisa em Caminhos de Pesquisa no Gerenciador de Soluções](media/search-paths-command.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Comando Adicionar Pasta ao Caminho de Pesquisa em Caminhos de Pesquisa no Gerenciador de Soluções](media/search-paths-command-2019.png)
::: moniker-end

Esse comando exibe um navegador no qual você pode selecionar a pasta a ser incluída.

Se a variável de ambiente `PYTHONPATH` já incluir as pastas que você deseja, use **Adicionar PYTHONPATH aos Caminhos de Pesquisa** como um atalho conveniente.

Depois que as pastas forem adicionadas aos caminhos de pesquisa, o Visual Studio usará esses caminhos para qualquer ambiente associado ao projeto. (Você poderá ver erros se o ambiente tiver base no Python 3, e você tentar adicionar um caminho de pesquisa aos módulos do Python 2.7.)

Os arquivos com uma extensão *.zip* ou *.egg* também podem ser adicionados como caminhos de pesquisa selecionando **Adicionar Arquivo Morto Zip ao Caminho de Pesquisa**. Assim como ocorre com pastas, o conteúdo desses arquivos é examinado e disponibilizado para o IntelliSense.

## <a name="see-also"></a>Confira também

- [Gerenciar ambientes do Python no Visual Studio](managing-python-environments-in-visual-studio.md)
- [Selecionar um interpretador para um projeto](selecting-a-python-environment-for-a-project.md)
- [Usar requirements.txt para dependências](managing-required-packages-with-requirements-txt.md)
- [Referência da janela de ambientes do Python](python-environments-window-tab-reference.md)
