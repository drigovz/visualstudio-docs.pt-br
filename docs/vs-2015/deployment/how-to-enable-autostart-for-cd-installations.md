---
title: Como habilitar a inicialização automática para instalações de CD | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c4bd14060517793d28e24818a051df63efb8f0e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153780"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Como habilitar o AutoStart para instalações por CD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao implantar um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo por meio de mídia removível, como CD-ROM ou DVD-ROM, você pode habilitar `AutoStart` para que o [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo seja iniciado automaticamente quando a mídia for inserida.  
  
 `AutoStart` pode ser habilitado na página **publicar** do designer de **projeto**.  
  
### <a name="to-enable-autostart"></a>Para habilitar o AutoStart  
  
1. Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2. Clique na guia **Publicar**.  
  
3. Clique no botão **Opções** .  
  
     A caixa de diálogo **Opções de publicação** é exibida.  
  
4. Clique em **Implantação**.  
  
5. Marque a caixa **de seleção para instalações de CD, iniciar a instalação automaticamente quando o CD for inserido** .  
  
     Um arquivo autorun. inf será copiado para o local de publicação quando o aplicativo for publicado.  
  
## <a name="see-also"></a>Consulte Também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como publicar um Aplicativo ClickOnce usando o Assistente de Publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
