---
title: Remover o Visual Studio
titleSuffix: ''
description: Aprenda a remover completamente o Visual Studio do seu computador, passo a passo.
ms.date: 12/19/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- uninstall
- uninstall Visual Studio
- remove
- remove Visual Studio
- cleanup
- cleanup Visual Studio
- clean up
- clean up Visual Studio
ms.assetid: 9c81a777-9c95-4934-b517-c60c6dc78799
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 98886df1c7fb09fa30d5c54abe19452780195b6a
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649203"
---
# <a name="remove-visual-studio"></a>Remover o Visual Studio

Se você sofrer um erro catastrófico e não puder reparar ou `InstallCleanup.exe` desinstalar o Visual Studio, você pode executar a ferramenta para remover arquivos de instalação e informações do produto para todas as instâncias instaladas do Visual Studio 2017 ou Visual Studio 2019.

> [!WARNING]
> Use a ferramenta InstallCleanup **apenas como último recurso** se o reparo ou a desinstalação falharem. Esta ferramenta pode desinstalar recursos de outras instalações do Visual Studio ou outros produtos, que também podem precisar ser reparados ou reinstalados.

## <a name="run-installcleanupexe"></a>Executar InstallCleanup.exe

Você pode usar qualquer um dos seguintes `InstallCleanup.exe` switches de linha de comando com a ferramenta:

| Opção | Comportamento |
| ------ | -------- |
| `-i`   | Este switch é o padrão se nenhum outro switch for aprovado. Ele remove apenas o diretório principal de instalação e as informações do produto. Use este switch se você pretende reinstalar a mesma `InstallCleanup.exe` versão do Visual Studio depois de executar a ferramenta. |
| `-f`   | Este switch remove o diretório principal de instalação, informações sobre o produto e a maioria dos outros recursos instalados fora do diretório de instalação, que também podem ser compartilhados com outras instalações do Visual Studio ou outros produtos. Use este interruptor se você pretende remover o Visual Studio sem reinstalá-lo mais tarde. |

Veja como executar a `InstallCleanup.exe` ferramenta:

1. Fechar o instalador do Visual Studio.
1. Abra um prompt de comando do administrador. Para abrir um prompt de comando de administrador, siga estas etapas:
   * Digite **cmd** na caixa "Digite aqui para pesquisar".
   * Clique com o botão direito do mouse em **Prompt de Comando** e escolha **Executar como administrador**.
1. Digite o caminho `InstallCleanup.exe` completo da ferramenta e adicione o switch de linha de comando que você preferir. Por padrão, o caminho da ferramenta é o seguinte. As aspas duplas encerram um comando contendo espaços:

   ```
   "C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe"
   ```

   > [!NOTE]
   > Se você não `InstallCleanup.exe` pode encontrar sob o diretório Visual Studio Installer, que está sempre localizado em `%ProgramFiles(x86)%\Microsoft Visual Studio`, aqui está o que fazer a seguir. Siga as instruções para [instalar o Visual Studio](install-visual-studio.md). Em seguida, quando a tela de seleção de carga de trabalho for exibida, feche a janela e siga os passos nesta página novamente.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Confira também

* [Instalar o Visual Studio](install-visual-studio.md)
* [Atualizar o Visual Studio](update-visual-studio.md)
* [Modificar o Visual Studio](modify-visual-studio.md)
* [Desinstalar o Visual Studio](uninstall-visual-studio.md)
