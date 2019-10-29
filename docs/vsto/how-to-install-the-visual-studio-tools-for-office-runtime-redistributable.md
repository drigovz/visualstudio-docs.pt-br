---
title: Como instalar o Ferramentas do Visual Studio para o Office Runtime Redistributable
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
ms.openlocfilehash: 801486e7c0abfa2cb91f7fb7237cf3a48e8bc916
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985915"
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>Como instalar o Ferramentas do Visual Studio para o Office Runtime Redistributable
  O tempo de execução das ferramentas do Visual Studio 2010 para Office deve ser instalado em cada computador que executa soluções criadas com o uso das ferramentas de desenvolvedor do Microsoft Office no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. O tempo de execução é instalado automaticamente quando você instala [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]e Microsoft Office. Para obter mais informações, consulte [Ferramentas do Visual Studio para cenários de instalação de tempo de execução do Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

[!include[Add-ins note](includes/addinsnote.md)]

 Talvez seja necessário seguir as instruções de instalação manual abaixo nas seguintes situações:

- Você precisa instalar o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] em um servidor. Por exemplo, você deseja usar a classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> para gerenciar soluções em nível de documento em um servidor.

- Você precisa instalar o tempo de execução em um computador que já tenha todos os outros pré-requisitos para as soluções do Office instaladas.

    > [!NOTE]
    > Você deve ser um administrador no computador de desenvolvimento para instalar o .NET Framework e o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].

## <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>Para instalar o Ferramentas do Visual Studio para o tempo de execução do Office

1. Instale o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior.

    - Para baixar o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], consulte [Microsoft .NET Framework 4 (instalador da Web)](https://www.microsoft.com/download/details.aspx?id=17851).

    - Para baixar o [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)], consulte [Microsoft .net o perfil do cliente do Framework 4 (instalador da Web)](https://www.microsoft.com/download/details.aspx?id=17113).

    - Para baixar o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], consulte [Microsoft .NET Framework 4,5](https://www.microsoft.com/download/details.aspx?id=30653).

2. Execute *vstor_redist. exe* para instalar o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].

     Você pode baixar esses arquivos de instalação do [Visual Studio 2010 Tools for Office Runtime](https://www.microsoft.com/download/details.aspx?id=56961). Os pré-requisitos para o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] correspondem aos pré-requisitos para o .NET Framework.

     O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] inclui pacotes de idiomas. Se a instalação do Windows for definida como um idioma diferente do inglês, você poderá exibir mensagens de tempo de execução no mesmo idioma usado para o Windows. Da mesma forma, se os usuários finais instalarem o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] e, em seguida, executarem suas soluções em instalações do Windows que são definidas para um idioma diferente do inglês, as mensagens de tempo de execução aparecerão no mesmo idioma que o Windows. Em alguns casos, talvez sejam necessários pacotes de idiomas adicionais. Por exemplo, você pode precisar de pacotes de idiomas adicionais se a cópia do Windows usar mais de uma configuração de idioma ou se você alternar para outro idioma depois que você já tiver instalado o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Você pode encontrar pacotes de idiomas em [Microsoft Visual Studio 2010 ferramentas para o pacote de idiomas do sistema Microsoft Office (tempo de execução da versão 4,0)](https://www.microsoft.com/download/details.aspx?id=54246).

## <a name="see-also"></a>Consulte também
- [Introdução &#40;ao desenvolvimento do Office no Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Configurar um computador para desenvolver soluções do Office](../vsto/configuring-a-computer-to-develop-office-solutions.md)
- [Como configurar um computador para desenvolver soluções do Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Como instalar assemblies de interoperabilidade primária do Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [Gerenciar documentos em um servidor usando a classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Implantar uma solução do Office](../vsto/deploying-an-office-solution.md)
