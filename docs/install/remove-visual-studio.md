---
title: Remover o Visual Studio
titleSuffix: ''
description: Saiba como remover completamente o Visual Studio de seu computador, passo a passo.
ms.date: 03/30/2019
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
author: heaths
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e363065d96169660817a548fb97d39f09cf679c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62810384"
---
# <a name="remove-visual-studio"></a>Remover o Visual Studio

Se você encontrar um erro fatal e não puder reparar ou desinstalar o Visual Studio, poderá executar a ferramenta `InstallCleanup.exe` para remover os arquivos de instalação e informações do produto de todas as instâncias instaladas do Visual Studio 2017 ou Visual Studio 2019. Essa ferramenta deverá ser executada somente como um último recurso se a reparação ou a desinstalação falharem. Ela poderá desinstalar recursos de outras instalações do Visual Studio ou outros produtos que, nesse caso, talvez também precisem ser reparados.

Nas instruções a seguir, você pode executar a ferramenta com diferentes opções de linha de comando com o seguinte comportamento:

| Alternar | Comportamento |
| ------ | -------- |
| `-i`   | Esta será a opção padrão se nenhuma outra opção for passada. Ela remove apenas o diretório de instalação principal e as informações do produto. Esse comportamento é preferível se você pretende reinstalar a mesma versão depois de executar a ferramenta `InstallCleanup.exe`. |
| `-f`   | Especificar essa opção remove o diretório de instalação principal, as informações do produto e a maioria dos outros recursos instalados fora do diretório de instalação que podem ser compartilhados com outras instalações do Visual Studio ou outros produtos. Esse comportamento é preferível se você pretende remover o Visual Studio sem instalá-lo novamente mais tarde. |

1. Fechar o instalador do Visual Studio.
2. Abrir um prompt de comando de administrador. Para abrir um prompt de comando de administrador, siga estas etapas:
   * Digite **cmd** na caixa "Digite aqui para pesquisar".
   * Clique com o botão direito em **Prompt de Comando**e em **Executar como administrador**.
3. Digite o caminho completo do utilitário `InstallCleanup.exe` e passe qualquer opção de linha de comando desejada. Por padrão, o caminho do utilitário é o seguinte:

   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```

Se não encontrar o `InstallCleanup.exe` no diretório do Instalador do Visual Studio (sempre localizado em `%ProgramFiles(x86)%\Microsoft Visual Studio`), siga as instruções de [instalação do Visual Studio](install-visual-studio.md) e quando a tela de seleção de carga de trabalho for exibida, feche a janela e siga as etapas anteriores novamente.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Consulte também

* [Instalar o Visual Studio](install-visual-studio.md)
* [Atualizar o Visual Studio](update-visual-studio.md)
* [Modificar o Visual Studio](modify-visual-studio.md)
* [Desinstalar o Visual Studio](uninstall-visual-studio.md)
