---
title: Diferenças entre a área restrita e soluções em Farm | Microsoft Docs
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
ms.openlocfilehash: 49dcd021e3f04d78af9d0ff50e7001dedcc73297
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867852"
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>Diferenças entre a área restrita e soluções em farm
  Quando você compila uma solução do SharePoint, implanta o servidor do SharePoint e um depurador é anexado para depurá-lo. O processo usado para depurar a solução depende da configuração da propriedade de solução de área restrita: solução de área restrita ou solução de farm.  
  
 Para obter mais informações, consulte [considerações sobre a solução em área restrita](../sharepoint/sandboxed-solution-considerations.md).  
  
## <a name="farm-solutions"></a>Soluções de farm
 Soluções de farm, que são hospedadas no processo de trabalho do IIS (W3WP.exe), execute o código que pode afetar o farm inteiro. Quando você depura um projeto do SharePoint cuja propriedade de solução de área restrita é definida como "solução de farm", o pool de aplicativos do IIS do sistema recicla antes que o SharePoint retira ou implanta o recurso para liberar todos os arquivos bloqueados pelo processo de trabalho do IIS. Somente o pool de aplicativos do IIS que atende a URL do site do projeto do SharePoint é reciclado.  
  
## <a name="sandboxed-solutions"></a>Soluções em área restrita
 Soluções em área restrita, que são hospedadas no processo de trabalho de solução de código do usuário do SharePoint (SPUCWorkerProcess.exe), execute o código que só pode afetar o conjunto de sites da solução. Como soluções em área restrita não são executados no processo de trabalho do IIS, deverá reiniciar nem o pool de aplicativos IIS nem o servidor IIS. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] anexa o depurador ao processo SPUCWorkerProcess que automaticamente dispara o serviço SPUserCodeV4 no SharePoint e controles. Não é necessário para o processo SPUCWorkerProcess reciclar para carregar a versão mais recente da solução.  
  
## <a name="either-type-of-solution"></a>Qualquer tipo de solução
 Com qualquer tipo de solução, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] também anexa o depurador para o navegador para habilitar a depuração de script do lado do cliente. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] usa o mecanismo para essa finalidade de depuração de script. Para habilitar a depuração de script, você deve alterar as configurações padrão do navegador quando for solicitado.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] anexa o depurador somente aos processos de W3WP ou SPUCWorkerProcess executando o site atual. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] também anexa o gerenciado COM Plus e mecanismos de depuração de fluxo de trabalho.  
  
## <a name="see-also"></a>Consulte também
 [Depurar soluções do SharePoint](../sharepoint/debugging-sharepoint-solutions.md)   
 [Compilar e depurar soluções do SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Considerações sobre a solução em área restrita](../sharepoint/sandboxed-solution-considerations.md)  
