---
title: Executar soluções em versões diferentes do Microsoft Office
description: Saiba como você pode executar versões de Microsoft Office soluções que foram criadas usando o Visual Studio 2010 e posterior.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], multiple Office versions
- Office applications [Office development in Visual Studio], multiple Office versions
- Office development in Visual Studio, multiple Office versions
- Office solutions [Office development in Visual Studio]
- multiple Office versions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4d70e61e318f0f6afd0a58ed35f912b6a5f2cda8
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523543"
---
# <a name="run-solutions-in-different-versions-of-microsoft-office"></a>Executar soluções em versões diferentes do Microsoft Office

## <a name="run-office-solutions-created-by-using-visual-studio-2010-and-above"></a>Executar soluções do Office criadas usando o Visual Studio 2010 e posterior

|Versão do Office direcionada ao modelo de projeto|.NET Framework de destino do projeto<sup>1</sup>|Versões do Office que podem executar a solução|Tempo de execução necessário no computador do usuário final|
|--------------------------------------------------------|------------------------------------------------------|--------------------------------------------------|-------------------------------------------|
|Office 2016 e [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office sistema<sup>2</sup>|Visual Studio 2010 Tools para Office Runtime|
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office sistema<sup>2</sup>|Visual Studio 2010 Tools para Office Runtime|
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|.NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Visual Studio 2010 Tools para Office Runtime|
|Sistema Microsoft Office 2007|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior,<br /><br /> ou<br /><br /> .NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> Sistema Microsoft Office 2007|Visual Studio 2010 Tools para Office Runtime|

 1. A versão .NET Framework que seu projeto tem como destino é necessária nos computadores dos usuários finais para que sua solução seja executada. Por exemplo, se o seu projeto tiver como alvo o .NET Framework 3,5, o .NET Framework 3,5 será necessário nos computadores dos usuários finais. Neste exemplo, a solução não será executada se apenas o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] estiver instalado nos computadores dos usuários finais.

 2. Nesse cenário, a solução será executada sem erros no sistema de Microsoft Office de 2007 somente se não usar recursos novos no [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] .

## <a name="run-office-solutions-created-by-using-versions-of-visual-studio-prior-to-visual-studio-2010"></a>Executar soluções do Office criadas usando versões do Visual Studio antes do Visual Studio 2010
 Microsoft Office aplicativos podem executar soluções criadas usando versões do Visual Studio antes do Visual Studio 2010. Em alguns casos, essas soluções exigem versões diferentes do [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Versões diferentes do [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] podem ser instaladas lado a lado no mesmo computador.

 A tabela a seguir mostra quais versões do Microsoft Office podem executar soluções criadas usando versões anteriores do Visual Studio e quais versões do [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] e os .NET Framework são necessários para cada solução.

|Edição do Visual Studio usada para criar a solução|Versão do Office direcionada ao modelo de projeto|Versões do Office que podem executar a solução|Tempo de execução necessário no computador do usuário final|Versão de .NET Framework necessária no computador do usuário final|
|----------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------|-------------------------------------------|----------------------------------------------------------|
|Visual Studio 2008 Professional<br /><br /> ou<br /><br /> Visual Studio Team System 2008|Sistema Microsoft Office 2007|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<sup>1</sup><br /><br /> Sistema Microsoft Office 2007|Visual Studio 2010 Tools for Office Runtime<sup>1</sup><br /><br /> ou<br /><br /> Ferramentas do Visual Studio para o sistema de Microsoft Office (versão 3,0 Runtime)|.NET Framework 3.5|
|Uma das seguintes edições do Visual Studio 2005 com VSTO 2005 SE<sup>2</sup> instalado:<br /><br /> -Visual Studio 2005 Tools for Office<br />-Visual Studio Team System 2005<br />-Visual Studio 2005 Professional|Sistema Microsoft Office 2007|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (somente 32 bits<sup>3</sup>)<br /><br /> Sistema Microsoft Office 2007|Tempo de execução das ferramentas do Visual Studio 2005 para Office Second Edition|.NET Framework 2,0, .NET Framework 3,0 ou .NET Framework 3,5|
|Qualquer uma das seguintes edições do Visual Studio:<br /><br /> -Visual Studio 2008 Professional<br />-Visual Studio Team System 2008<br />-Visual Studio 2005 Tools for Office (com ou sem o VSTO 2005 SE<sup>2</sup> instalado)<br />-Visual Studio Team System 2005 (com ou sem o VSTO 2005 SE<sup>2</sup> instalado)<br />-Visual Studio 2005 Professional com VSTO 2005 SE<sup>2</sup> instalado|Microsoft Office 2003|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (somente 32 bits<sup>3</sup>)<br /><br /> Sistema Microsoft Office 2007<br /><br /> Microsoft Office 2003|Tempo de execução das ferramentas do Visual Studio 2005 para Office Second Edition|.NET Framework 2,0, .NET Framework 3,0 ou .NET Framework 3,5|

 1. [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] os aplicativos incluem o tempo de execução das ferramentas do Visual Studio 2010 para Office. Portanto, esses aplicativos sempre usam o tempo de execução das ferramentas do Visual Studio 2010 para Office em vez de Ferramentas do Visual Studio para o sistema Microsoft Office (tempo de execução da versão 3,0) nesse cenário. Os aplicativos no sistema de Microsoft Office de 2007 podem usar o tempo de execução das ferramentas do Visual Studio 2010 para Office ou o Ferramentas do Visual Studio para o sistema de Microsoft Office (versão de tempo de execução 3,0).

 2. O VSTO 2005 SE é um complemento gratuito do Visual Studio que fornece modelos de projeto de suplemento do VSTO para Microsoft Office 2003 e o sistema de Microsoft Office 2007. Ele pode ser instalado com o Visual Studio 2005 Professional, o Visual Studio 2005 Tools for Office ou uma edição no Visual Studio Team System 2005. Para obter mais informações, consulte [Visual Studio 2005 Tools para Office Second Edition](https://developer.microsoft.com/office/docs).

 3. As soluções do Office que exigem o tempo de execução das ferramentas do Visual Studio 2005 para Office Second Edition não são compatíveis com as versões de 64 bits do [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] e do [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] . Para executar essas soluções na edição de 64 bits do [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ou do [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] , você deve atualizar o projeto do para [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] o ou para um projeto do Visual Studio 2008 que tenha como alvo o sistema 2007 Microsoft Office.

## <a name="see-also"></a>Veja também
- [Projetar e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md)
- [Visão geral do Ferramentas do Visual Studio para Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Ferramentas do Visual Studio para cenários de instalação do Office Runtime](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)
- [Configurar um computador para desenvolver soluções do Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)
