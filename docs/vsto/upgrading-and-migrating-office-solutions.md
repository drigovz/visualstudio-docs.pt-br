---
title: Atualizar e migrar soluções do Office
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], upgrading
- Office projects [Office development in Visual Studio], upgrading
- upgrading applications [Office development in Visual Studio]
- upgrading Office solutions in Visual Studio
- migrating Office solutions in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c00d160d67fbcb5e64b6b5bd22cd886b1f4010e6
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985527"
---
# <a name="upgrade-and-migrate-office-solutions"></a>Atualizar e migrar soluções do Office
  Se você tiver um projeto Microsoft Office que foi criado em uma versão anterior do Visual Studio, deverá atualizar o projeto para usá-lo em versões atuais do Visual Studio. Para atualizar um projeto Microsoft Office, abra-o em uma versão do Visual Studio que inclua as ferramentas de desenvolvedor de Microsoft Office. Para obter mais informações sobre as versões do Visual Studio que incluem as ferramentas de desenvolvedor Microsoft Office, consulte [configurar um computador para desenvolver soluções do Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

[!include[Add-ins note](includes/addinsnote.md)]

> [!NOTE]
> O Visual Studio não pode atualizar projetos de modelo de formulário do InfoPath que foram criados usando versões anteriores do Visual Studio. Esses tipos de projetos não têm suporte na versão atual do Visual Studio.

## <a name="changes-to-upgraded-projects"></a>Alterações em projetos atualizados
 Quando você atualiza um projeto Microsoft Office, o Visual Studio modifica o projeto para direcionar os seguintes itens:

- O tempo de execução das ferramentas do Visual Studio 2010 para Office. Para obter mais informações, consulte [visão geral do ferramentas do Visual Studio para Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).

- As referências do assembly atual.

- Uma versão do .NET Framework que é compatível com o tipo de projeto (quando você atualiza para Visual Studio 2013 somente).

- Uma versão do Microsoft Office que é compatível com o tipo de projeto (quando você atualiza para Visual Studio 2013 somente).

## <a name="assembly-references"></a>Referências de assembly
 O Visual Studio atualiza as seguintes referências de assembly no projeto:

- Microsoft Office assemblies de interoperabilidade primária (PIAs).

- Assemblies no [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Para obter mais informações sobre esses assemblies, consulte [a visão geral do ferramentas do Visual Studio for Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).

- Versões novas ou atualizadas de assemblies dependentes.

## <a name="targeted-net-framework"></a>.NET Framework de destino
 Quando você atualiza um projeto para Visual Studio 2013, o Visual Studio modifica o projeto para direcionar o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] ou o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. A versão do .NET Framework direcionada ao projeto depende de qual versão do Office está instalada em seu computador. Se [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] estiver instalado, o Visual Studio modificará o projeto para direcionar o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Caso contrário, o Visual Studio modificará o projeto para direcionar o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].

> [!NOTE]
> Talvez seja necessário executar algumas etapas adicionais para executar uma solução redirecionada em computadores de usuário final e de desenvolvimento, e seu projeto não será mais compilado se usar determinados recursos. Para obter mais informações, consulte [migrar soluções do Office para o .NET Framework 4 ou posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

 Se você direcionar o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior em um projeto do Office, poderá usar alguns recursos que não estão disponíveis ao direcionar o .NET Framework 3,5. Para obter mais informações, consulte [design e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md).

## <a name="targeted-office-application"></a>Aplicativo do Office de destino
 Quando você atualiza um projeto do Office para Visual Studio 2013, o Visual Studio modifica o projeto para direcionar uma versão do Microsoft Office que é compatível com o tipo de projeto, como um projeto de personalização no nível de documento ou um projeto de suplemento do VSTO.

 Os projetos do Office no Visual Studio 2013 podem direcionar [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] aplicativos. O Visual Studio modifica o projeto para direcionar a versão mais recente do Office que você instalou. Se nenhuma dessas versões do Office estiver instalada, o Visual Studio não atualizará o projeto.

> [!NOTE]
> Se você atualizar um projeto de suplemento do VSTO para o destino [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ou posterior, verifique se o manipulador de eventos `ThisAddIn_Startup` do suplemento do VSTO não contém o código que acessa um documento no aplicativo. Para obter mais informações, consulte [acessar um documento quando o aplicativo do Office for iniciado](../vsto/programming-vsto-add-ins.md#AccessingDocuments).

 Para personalizações em nível de documento, [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] converte documentos em um projeto que têm um formato binário, como documentos que têm uma extensão *. xls* ou *. doc* , para o formato XML aberto do Office. Para obter mais informações sobre o XML aberto, consulte [introdução às novas extensões de nome de arquivo e formatos XML abertos](https://support.office.com/en-nz/article/Introduction-to-new-file-name-extensions-eca81dcb-5626-4e5b-8362-524d13ae4ec1).

> [!NOTE]
> Marcas inteligentes são preteridas no Excel 2010 e no Word 2010. Portanto, se sua solução usar marcas inteligentes, você deverá removê-las antes de poder testá-las e depurá-las no Visual Studio 2013 ou no Visual Studio 2015.

## <a name="upgrade-microsoft-office-2003-projects"></a>Atualizar Microsoft Office projetos do 2003
 Há algumas considerações adicionais para atualizar as personalizações em nível de documento e os suplementos do VSTO que visam Microsoft Office 2003.

### <a name="document-level-projects"></a>Projetos de nível de documento
 Se o documento no projeto contiver controles Windows Forms, você também deverá ter o tempo de execução das ferramentas do Visual Studio 2005 para Office Second Edition instalado antes de atualizar o projeto. Se esta versão do tempo de execução não estiver instalada no computador de desenvolvimento antes de atualizar o projeto, o projeto atualizado poderá conter erros de compilação ou de tempo de execução. Depois de concluir a atualização do projeto, você poderá desinstalar o tempo de execução das ferramentas do Visual Studio 2005 para Office Second Edition do computador de desenvolvimento se ele não estiver sendo usado por outras soluções do Office. Esta versão do tempo de execução está disponível como um pacote redistribuível do centro de download da Microsoft em [Microsoft Visual Studio 2005 Tools for Office Second Edition Runtime (VSTO 2005 se) (x86)](https://www.microsoft.com/download/details.aspx?id=2392).

### <a name="vsto-add-in-projects"></a>Projetos de suplemento do VSTO
 Se o arquivo de solução do projeto original incluísse um projeto de instalação ou de edição limitada do InstallShield que foi configurado para instalar o suplemento do VSTO, o Visual Studio atualizará o projeto, mas não fará nenhuma alteração adicional no projeto. Se você quiser continuar usando um arquivo de Windows Installer para implantar o suplemento do VSTO, você deve modificar o projeto de instalação ou do InstallShield Limited Edition para instalar novos pré-requisitos, como o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], o tempo de execução das ferramentas do Visual Studio 2010 para Office e, opcionalmente, o assemblies de interoperabilidade primária referenciados pelo seu suplemento do VSTO. Para obter mais informações, consulte [implantar uma solução do Office usando Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).

 Se você quiser usar o ClickOnce para implantar o suplemento do VSTO, poderá excluir totalmente o projeto de instalação ou do InstallShield Limited Edition. Para obter mais informações sobre como implantar suplementos do VSTO usando o ClickOnce, consulte [implantar uma solução do Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Consulte também
- [Como: atualizar soluções do Office](https://msdn.microsoft.com/a269e539-b717-4680-a568-2152b070347e)
- [Migrar soluções do Office para o .NET Framework 4 ou posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Atualização do projeto, caixa de diálogo opções](../vsto/project-upgrade-options-dialog-box.md)
