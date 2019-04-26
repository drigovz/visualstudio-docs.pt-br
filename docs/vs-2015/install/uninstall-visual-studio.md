---
title: Desinstalar o Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- uninstalling
- uninstalling visual studio
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
caps.latest.revision: 9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: ed9d33501644c6fa7252dffa758f92c0919653b1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546896"
---
# <a name="uninstall-visual-studio"></a>Desinstalar o Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obter a documentação mais recente do Visual Studio, confira [Desinstalar o Visual Studio](/visualstudio/install/uninstall-visual-studio).

Esta página guia você pela desinstalação do Visual Studio 2015, uma versão anterior de nosso pacote integrado de ferramentas de produtividade para desenvolvedores.

## <a name="uninstall-visual-studio-by-using-the-standard-uninstallation-method"></a>Desinstalar o Visual Studio usando o método de desinstalação "padrão"

1. No **Painel de Controle**, na página **Programas e Recursos**, escolha a edição do produto que você deseja desinstalar e, em seguida, escolha **Alterar**.

2. No Assistente de instalação, escolha **Desinstalar**, escolha **Sim** e, em seguida, siga as instruções restantes no assistente.

   Esse padrão, ou método padrão, manterá alguns itens da primeira instalação do Visual Studio originalmente instalada (por exemplo, o Microsoft .NET Framework, Microsoft Visual C++ Redistributables, Microsoft SQL Server etc.).   Deixamos esses itens instalados porque muitos outros aplicativos dependem deles. No entanto, se você quiser removê-los também, selecione a entrada correspondente em **Programas e Recursos**e remova cada um individualmente.

## <a name="uninstall-visual-studio-and-all-other-related-files-that-is-to-uninstall-almost-everything"></a>Desinstalar o Visual Studio e todos os outros arquivos relacionados (ou seja, desinstalar quase tudo)

1. Localize o arquivo .exe do Visual Studio (por exemplo, localize "vs_enterprise.exe").

    > [!NOTE]
    > O arquivo deve estar em uma subpasta de "%ProgramData%\Package Cache", por exemplo: C:\ProgramData\Package Cache\\{37e19555-e88d-4aed-9d42-82d0784d2b79}\vs_enterprise.exe

2. Execute o arquivo .exe usando os parâmetros /uninstall /force command-line.

     Por exemplo, execute ```vs_enterprise.exe /uninstall /force```, que removerá o Visual Studio e a maioria dos componentes principais deixados para trás em uma desinstalação padrão. No entanto, isso não removerá todo o conteúdo adicional que os complementos e extensões do Visual Studio podem instalar (por exemplo, atualizações do Visual Studio e outros componentes opcionais).

    > [!TIP]
    > Como alternativa, você pode usar a ferramenta "**Desinstalador Total**" para remover tudo o que o Visual Studio ou as atualizações dele podem ter instalado. Ou seja, qualquer versão do Visual Studio 2013 ou posterior. Para saber mais, confira a [Ferramenta de desinstalação do Visual Studio](https://github.com/Microsoft/VisualStudioUninstaller/releases) no GitHub.

## <a name="uninstall-visual-studio-in-silent-or-passive-modes-that-is-to-uninstall-from-source"></a>Desinstalar o Visual Studio nos modos sem confirmação ou passivo (isto é, desinstalação da origem)

1. No computador onde o Visual Studio está instalado, abra o prompt de comando do Windows.

2. Digite os seguintes parâmetros:

     *DVDRoot* \\<Arquivo de Instalação\> \</quiet&#124;/passive> [/norestart]/uninstall

## <a name="roll-back-to-a-previous-version-or-release-of--visual-studio"></a>Reverter para uma versão anterior do Visual Studio

1. Desinstale o Visual Studio usando qualquer um dos métodos listados neste tópico.

   > [!WARNING]
   > Desinstalar uma versão atual do Visual Studio (ou uma atualização do Visual Studio) e, em seguida, instalar uma versão anterior pode não funcionar conforme o esperado.
   >
   > O resultado depende de qual versão do Visual Studio você instalou, quais versões de seus componentes estão instaladas, quais produtos instalados podem ter dependências ou a versão do Visual Studio ou seus componentes e, finalmente, qual versão anterior do Visual Studio você planeja instalar ou reinstalar.  Devido a todas essas variáveis, uma desinstalação padrão normalmente deixará para trás componentes que podem não funcionar com as versões anteriores do Visual Studio.
   >
   > Portanto, para obter melhores resultados, é recomendável usar a [Ferramenta de desinstalação do Visual Studio](https://github.com/Microsoft/VisualStudioUninstaller/releases).

2. Instale ou reinstale a versão anterior do Visual Studio que você quer usar.

   Mesmo se você instalar uma versão anterior do Visual Studio, o programa de instalação pode ainda tentar usar uma versão mais recente, se houver uma disponível. Para obter informações detalhadas, confira o tópico [Como instalar uma versão específica do Visual Studio](../install/how-to-install-a-specific-release-of-visual-studio.md).

## <a name="see-also"></a>Consulte também

- [Instalar o Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx)