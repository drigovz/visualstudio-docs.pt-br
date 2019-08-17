---
title: 'Como: Instalar o Ferramentas do Visual Studio para o Office Runtime Redistributable'
titleSuffix: ''
ms.custom: seodec18
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio]
- installing Office development tools in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5d9bb53fbdc3d6766dab47c654f0a43ad902b2f3
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551830"
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>Como: Instalar o Ferramentas do Visual Studio para o Office Runtime Redistributable
  O tempo de execução das ferramentas do Visual Studio 2010 para Office deve ser instalado em cada computador que executa soluções criadas com o uso das ferramentas [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]de desenvolvedor do Microsoft Office no. O tempo de execução é instalado automaticamente quando [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]você instala o e o Microsoft Office. Para obter mais informações, consulte [Ferramentas do Visual Studio para cenários de instalação de tempo de execução do Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

[!include[Add-ins note](includes/addinsnote.md)]

 Talvez seja necessário seguir as instruções de instalação manual abaixo nas seguintes situações:

- Você precisa instalar o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] em um servidor. Por exemplo, você deseja usar a <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe para gerenciar soluções em nível de documento em um servidor.

- Você precisa instalar o tempo de execução em um computador que já tenha todos os outros pré-requisitos para as soluções do Office instaladas.

    > [!NOTE]
    > Você deve ser um administrador no computador de desenvolvimento para instalar o .NET Framework e o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].

## <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>Para instalar o Ferramentas do Visual Studio para o tempo de execução do Office

1. Instale o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior.

    - Para baixar o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], consulte [Microsoft .NET Framework 4 (instalador da Web)](http://go.microsoft.com/fwlink/?LinkId=178957).

    - Para baixar o [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)], consulte [Microsoft .net o perfil do cliente do Framework 4 (instalador da Web)](http://go.microsoft.com/fwlink/?LinkId=178958).

    - Para baixar o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], consulte [Microsoft .NET Framework 4,5](http://www.microsoft.com/download/details.aspx?id=30653).

2. Execute *vstor_redist. exe* para instalar o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].

     Você pode baixar esses arquivos de instalação do [Visual Studio 2010 Tools for Office Runtime](http://go.microsoft.com/fwlink/?LinkId=140384). Os pré-requisitos para a [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] correspondência dos pré-requisitos para o .NET Framework.

     O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] inclui pacotes de idiomas. Se a instalação do Windows for definida como um idioma diferente do inglês, você poderá exibir mensagens de tempo de execução no mesmo idioma usado para o Windows. Da mesma forma, se os usuários [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] finais instalarem o e executarem suas soluções em instalações do Windows definidas para um idioma diferente do inglês, as mensagens de tempo de execução aparecerão no mesmo idioma que o Windows. Em alguns casos, talvez sejam necessários pacotes de idiomas adicionais. Por exemplo, você pode precisar de pacotes de idiomas adicionais se sua cópia do Windows usar mais de uma configuração de idioma ou se você alternar para outro idioma depois de instalar [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]o. Você pode encontrar pacotes de idiomas em [Microsoft Visual Studio 2010 ferramentas para o pacote de idiomas do sistema Microsoft Office (tempo de execução da versão 4,0)](http://go.microsoft.com/fwlink/?LinkId=140386).

## <a name="see-also"></a>Consulte também
- [Introdução &#40;ao desenvolvimento do Office no Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Configurar um computador para desenvolver soluções do Office](../vsto/configuring-a-computer-to-develop-office-solutions.md)
- [Como: Configurar um computador para desenvolver soluções do Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Como: Instalar assemblies de interoperabilidade primária do Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [Gerenciar documentos em um servidor usando a classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Implantar uma solução do Office](../vsto/deploying-an-office-solution.md)
