---
title: 'Como: Definir a publicação do ClickOnce versão | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7908bb88e13dff34721b7c6419d0a7f036be68d1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54923578"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Como: Definir a versão da publicação do ClickOnce
O [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` propriedade determina se o aplicativo que você está publicando será tratado como uma atualização. É incrementado a cada versão do tempo, o aplicativo será publicado como uma atualização.  
  
 O `Publish Version` propriedade pode ser definida na **Publish** página da **Designer de projeto**.  
  
> [!NOTE]
>  Há uma opção de projeto automaticamente incrementará o `Publish Version` propriedade cada vez que o aplicativo é publicado; essa opção é habilitada por padrão. Para obter mais informações, confira [Como: Incrementar automaticamente a versão de publicação do ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).  
  
### <a name="to-change-the-publish-version"></a>Para alterar a versão de publicação  
  
1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2.  Clique o **publicar** guia.  
  
3.  No **Publish Version** campo, incremente o **principais**, **secundárias**, **Build**, ou **revisão** versão números.  
  
    > [!NOTE]
    >  Você nunca deve diminuir um número de versão; Isso pode gerar comportamento de atualização imprevisíveis.  
  
## <a name="see-also"></a>Consulte também  
 [Escolher uma estratégia de atualização do ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Como: Incrementar automaticamente a versão de publicação do ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [Publicar aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como: Publicar um aplicativo ClickOnce usando o assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)