---
title: 'Como: Habilitar o AutoStart para instalações por CD | Microsoft Docs'
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153780"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Como: Habilitar o AutoStart para instalações do CD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao implantar uma [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo por meio de uma mídia removível, como CD-ROM ou DVD-ROM, você pode habilitar `AutoStart` para que o [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo seja iniciado automaticamente quando a mídia for inserida.  
  
 `AutoStart` pode ser habilitada na **Publish** página do **Designer de projeto**.  
  
### <a name="to-enable-autostart"></a>Para habilitar o AutoStart  
  
1. Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2. Clique o **publicar** guia.  
  
3. Clique o **opções** botão.  
  
     O **opções de publicação** caixa de diálogo é exibida.  
  
4. Clique em **implantação**.  
  
5. Selecione o **instalações para CD, iniciar automaticamente a instalação quando o CD é inserido** caixa de seleção.  
  
     Um arquivo Autorun será copiado para o local de publicação quando o aplicativo é publicado.  
  
## <a name="see-also"></a>Consulte também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como: Publicar um aplicativo ClickOnce usando o assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
