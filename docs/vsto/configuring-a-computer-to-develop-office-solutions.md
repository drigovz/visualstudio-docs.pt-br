---
title: Configurar um computador para desenvolver soluções do Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7a0304c217599e790b8cfa9e738245927336470e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88801835"
---
# <a name="configure-a-computer-to-develop-office-solutions"></a>Configurar um computador para desenvolver soluções do Office

Para criar suplementos e personalizações do VSTO para Microsoft Office, instale uma versão com suporte do Visual Studio, o .NET Framework e o Microsoft Office.

|Software|Versões com suporte|
|--------------|------------------------|
|Visual Studio 2017| Qualquer edição com a carga de trabalho de **desenvolvimento do Office/SharePoint** .|
|.NET Framework|-O .NET Framework 4 ou posterior.|
|Microsoft Office|<ul><li>Qualquer edição do pacote do Office, incluindo aplicativos Microsoft 365 para empresas.</li><li>Qualquer uma das aplicações autônomas seguintes:<br /><br /> <ul><li>Excel</li><li>InfoPath (somente Office 2013 e Office 2010)</li><li>Outlook</li><li>PowerPoint</li><li>Project</li><li>Visio</li><li>Word</li></ul></li></ul><br /> O Visual Basic for Applications (VBA) deve ser instalado como parte do Office. **Importante:** Não há suporte para versões de clique para executar de aplicativos do Office 2010.|

Para obter as etapas de instalação detalhadas, consulte [como configurar um computador para desenvolver soluções do Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Se os modelos de projeto não aparecerem ou não funcionarem no Visual Studio

Se você instalar uma versão com suporte do Visual Studio, os .NET Framework e Microsoft Office, mas os modelos de projeto do Office não aparecerem na caixa de diálogo **novo projeto** do Visual Studio, ou se você receber um erro ao tentar usar um, verifique o seguinte:

- Certifique-se de que o Microsoft Office Developer Tools esteja instalado no computador.

     O Office Developer Tools é um componente opcional do Visual Studio, mas eles são instalados automaticamente juntamente com o Visual Studio. Se você personalizar a instalação do Visual Studio especificando quais recursos instalar, certifique-se de escolher **Microsoft Office ferramentas para desenvolvedores** durante a instalação para instalar as ferramentas.

     Para certificar-se de que essas ferramentas estejam instaladas, inicie o programa de instalação do Visual Studio e escolha o botão **Modificar** . Marque a caixa de seleção **Microsoft Office ferramentas para desenvolvedores** e, em seguida, escolha o botão **Atualizar** .

- Certifique-se de que você não está executando uma versão do Office que foi entregue pelo clique para executar. Consulte [como: verificar se o Outlook é um aplicativo de clique para executar em um computador](/previous-versions/office/developer/office-2010/ff864733(v=office.14)).

- Verifique se você está executando apenas uma versão do Microsoft Office.

Se você continuar a ter problemas, consulte [suporte adicional para erros em soluções do Office](../vsto/additional-support-for-errors-in-office-solutions.md).

## <a name="see-also"></a>Confira também
- [Introdução &#40;desenvolvimento do Office no Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Como configurar um computador para desenvolver soluções do Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Como instalar o Ferramentas do Visual Studio para o Office Runtime Redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Como instalar assemblies de interoperabilidade primária do Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [Recursos disponíveis pelo aplicativo do Office e tipo de projeto](../vsto/features-available-by-office-application-and-project-type.md)