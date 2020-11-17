---
title: Diferenças entre as soluções de área restrita e de farm | Microsoft Docs
description: Entenda as diferenças entre as soluções de área restrita e de farm. Saiba como o Visual Studio aborda a depuração com qualquer tipo de solução.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 25c1c9047ba9e38e3e652abcbe92ce6575d7b750
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672776"
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>Diferenças entre soluções de área restrita e de farm
  Quando você compila uma solução do SharePoint, ela é implantada no servidor do SharePoint e um depurador é anexado para depurá-lo. O processo usado para depurar a solução depende da configuração da propriedade de solução de área restrita: solução de área restrita ou solução de farm.

 Para obter mais informações, consulte [Considerações sobre a solução em área restrita](../sharepoint/sandboxed-solution-considerations.md).

## <a name="farm-solutions"></a>Soluções de farm
 As soluções de farm, que são hospedadas no processo de trabalho do IIS (W3WP.exe), executam o código que pode afetar todo o farm. Quando você depura um projeto do SharePoint cuja propriedade de solução de área restrita está definida como "solução de farm", o pool de aplicativos do IIS do sistema é reciclado antes que o SharePoint retraia ou implante o recurso para liberar todos os arquivos bloqueados pelo processo de trabalho do IIS. Somente o pool de aplicativos do IIS que serve a URL do site do projeto do SharePoint é reciclado.

## <a name="sandboxed-solutions"></a>Soluções em área restrita
 As soluções em área restrita, que são hospedadas no processo de trabalho da solução de código de usuário do SharePoint (SPUCWorkerProcess.exe), executam o código que só pode afetar o conjunto de sites da solução. Como as soluções em área restrita não são executadas no processo de trabalho do IIS, nem o pool de aplicativos do IIS nem o servidor IIS devem ser reiniciados. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] anexa o depurador ao processo SPUCWorkerProcess que o serviço SPUserCodeV4 no SharePoint dispara e controla automaticamente. Não é necessário que o processo SPUCWorkerProcess seja reciclado para carregar a versão mais recente da solução.

## <a name="either-type-of-solution"></a>Qualquer tipo de solução
 Com qualquer tipo de solução, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] o também anexa o depurador ao navegador para habilitar a depuração de script do lado do cliente. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] usa o mecanismo de depuração de script para essa finalidade. Para habilitar a depuração de script, você deve alterar as configurações padrão do navegador quando solicitado.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] anexa o depurador somente aos processos W3WP ou SPUCWorkerProcess que executam o site atual. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] também anexa os mecanismos gerenciados COM e depuração de fluxo de trabalho.

## <a name="see-also"></a>Veja também
- [Depurar soluções do SharePoint](../sharepoint/debugging-sharepoint-solutions.md)
- [Compilar e depurar soluções do SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Considerações sobre a solução em área restrita](../sharepoint/sandboxed-solution-considerations.md)
