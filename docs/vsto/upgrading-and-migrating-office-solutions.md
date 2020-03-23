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
ms.openlocfilehash: 5e421d6e4ee94d9974c0a0583db1fb495c72593e
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416530"
---
# <a name="upgrade-and-migrate-office-solutions"></a>Atualizar e migrar soluções do Office
  Se você tem um projeto do Microsoft Office que foi criado em uma versão anterior do Visual Studio, você deve atualizar o projeto para usá-lo nas versões atuais do Visual Studio. Para atualizar um projeto do Microsoft Office, abra-o em uma versão do Visual Studio que inclui as ferramentas de desenvolvedor do Microsoft Office. Para obter mais informações sobre as versões do Visual Studio que incluem as ferramentas de desenvolvedor do Microsoft Office, consulte [Configurar um computador para desenvolver soluções do Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

[!include[Add-ins note](includes/addinsnote.md)]

> [!NOTE]
> O Visual Studio não pode atualizar os projetos de modelo de formulário do InfoPath que foram criados usando versões anteriores do Visual Studio. Esses tipos de projetos não são suportados no lançamento atual do Visual Studio.

## <a name="changes-to-upgraded-projects"></a>Alterações em projetos atualizados
 Quando você atualiza um projeto do Microsoft Office, o Visual Studio modifica o projeto para segmentar os seguintes itens:

- O Visual Studio 2010 Tools for Office runtime. Para obter mais informações, consulte [visual studio tools para visão geral do office runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).

- As referências de montagem atuais.

- Uma versão do .NET Framework que é suportada pelo tipo de projeto (quando você atualiza apenas para o Visual Studio 2013).

- Uma versão do Microsoft Office que é suportada pelo tipo de projeto (quando você atualiza apenas para o Visual Studio 2013).

## <a name="assembly-references"></a>Referências de assembly
 O Visual Studio atualiza as seguintes referências de montagem no projeto:

- Conjuntos de interop primários do Microsoft Office (PIAs).

- Assembléias no [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Para obter mais informações sobre essas montagens, consulte [visual studio tools para visão geral do office runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).

- Versões novas ou atualizadas de conjuntos dependentes.

## <a name="targeted-net-framework"></a>Quadro .NET direcionado
 Quando você atualiza um projeto para o Visual Studio 2013, [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]Visual Studio modifica o projeto para direcionar o ou o . A versão do framework .NET visada pelo projeto depende de qual versão do Office está instalada no seu computador. Se [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] for instalado, o Visual Studio modifica [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]o projeto para direcionar o . Caso contrário, o Visual Studio modifica [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]o projeto para direcionar o .

> [!NOTE]
> Você pode precisar executar algumas etapas adicionais para executar uma solução redirecionada em computadores de desenvolvimento e usuário final, e seu projeto não será mais compilado se ele usar certos recursos. Para obter mais informações, consulte [as soluções do Migrate Office para o .NET Framework 4 ou posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

 Se você [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] direcionar o projeto ou mais tarde em um projeto do Office, você poderá usar alguns recursos que não estão disponíveis quando você mira o .NET Framework 3.5. Para obter mais informações, consulte [Design e crie soluções do Office](../vsto/designing-and-creating-office-solutions.md).

## <a name="targeted-office-application"></a>Aplicativo do Office direcionado
 Quando você atualiza um projeto do Office para o Visual Studio 2013, o Visual Studio modifica o projeto para direcionar uma versão do Microsoft Office que é suportada pelo tipo de projeto, como um projeto de personalização em nível de documento ou projeto de complemento VSTO.

 Projetos de escritório no Visual Studio [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] 2013 podem segmentar e aplicativos. O Visual Studio modifica o projeto para atingir a versão mais recente do escritório que você instalou. Se nenhuma dessas versões do Office for instalada, o Visual Studio não atualizará o projeto.

> [!NOTE]
> Se você atualizar um projeto de [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] complemento VSTO para `ThisAddIn_Startup` segmentação ou posterior, certifique-se de que o manipulador de eventos do Add-in VSTO não contenha código que acessa um documento no aplicativo. Para obter mais informações, consulte [Acesse um documento quando o aplicativo do Office for iniciado](../vsto/programming-vsto-add-ins.md#AccessingDocuments).

 Para personalizações em [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] nível de documento, converte documentos em um projeto com um formato binário, como documentos que tenham uma extensão *.xls* ou *.doc,* para o formato Office Open XML. Para obter mais informações sobre o Open XML, consulte [Introdução a novas extensões de nome de arquivo e formatos Open XML](https://support.office.com/en-nz/article/Introduction-to-new-file-name-extensions-eca81dcb-5626-4e5b-8362-524d13ae4ec1).

> [!NOTE]
> As marcas inteligentes serão preteridas no Excel 2010 e no Word 2010. Portanto, se sua solução usa tags inteligentes, você deve removê-las antes de testá-las e depura-las no Visual Studio 2013 ou visual Studio 2015.

## <a name="upgrade-microsoft-office-2003-projects"></a>Atualizar projetos do Microsoft Office 2003
 Existem algumas considerações adicionais para atualizar personalizações em nível de documento e complementos VSTO que visam o Microsoft Office 2003.

### <a name="document-level-projects"></a>Projetos em nível de documento
 Se o documento no projeto contiver os controles do Windows Forms, você também deve ter as ferramentas do Visual Studio 2005 para office second edition runtime instaladas antes de atualizar o projeto. Se esta versão do tempo de execução não estiver instalada no computador de desenvolvimento antes de atualizar o projeto, o projeto atualizado pode conter erros de compilação ou tempo de execução. Depois de terminar de atualizar o projeto, você pode desinstalar o Visual Studio 2005 Tools for Office Second Edition Runtime a partir do computador de desenvolvimento se ele não estiver sendo usado por nenhuma outra solução do Office. Esta versão do tempo de execução está disponível como um pacote avermelhado do Microsoft Download Center no [Microsoft Visual Studio 2005 Tools for Office Second Edition Runtime (VSTO 2005 SE) (x86)](https://www.microsoft.com/download/details.aspx?id=2392).

### <a name="vsto-add-in-projects"></a>Projetos de complemento vsto
 Se o arquivo de solução do seu projeto original incluísse um projeto Setup ou InstallShield Limited Edition configurado para instalar o Complemento DO VSTO, o Visual Studio atualizaria o projeto, mas não fará mais alterações no projeto. Se você quiser continuar usando um arquivo do Windows Installer para implantar seu Complemento VSTO, você deve modificar o projeto [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]Setup ou InstallShield Limited Edition para instalar novos pré-requisitos, como o , o Visual Studio 2010 Tools for Office Runtime e, opcionalmente, os conjuntos de interop principais referenciados pelo complemento do VSTO. Para obter mais informações, consulte [Implantar uma solução do Office usando o Windows Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

 Se você quiser usar o ClickOnce para implantar o complemento do VSTO, você pode excluir totalmente o projeto Setup ou InstallShield Limited Edition. Para obter mais informações sobre a implantação de complementos VSTO usando o ClickOnce, consulte [Implantar uma solução do Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Confira também
- [Como: Atualizar soluções do Office](https://msdn.microsoft.com/a269e539-b717-4680-a568-2152b070347e)
- [Migrar as soluções do Office para o Quadro .NET 4 ou posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Atualização de projeto, caixa de diálogo opções](../vsto/project-upgrade-options-dialog-box.md)
