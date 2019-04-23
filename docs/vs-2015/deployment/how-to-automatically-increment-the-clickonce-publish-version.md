---
title: 'Como: Automaticamente incrementar a publicação do ClickOnce versão | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ab2dc62add13db9af1186a8974ffe5694a98e62e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60083485"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Como: Incrementar automaticamente a versão de publicação do ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao publicar uma [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo, alterando o `Publish Version` propriedade faz com que o aplicativo a ser publicado como uma atualização. Por padrão, o Visual Studio incrementa automaticamente o `Revision` número das `Publish Version` cada vez que você publica o aplicativo.  
  
 Você pode desativar esse comportamento na **Publish** página do **Designer de projeto**.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-disable-automatically-incrementing-the-publish-version"></a>Para desabilitar automaticamente incrementando a versão de publicação  
  
1. Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2. Clique o **publicar** guia.  
  
3. No **Publish Version** seção, desmarque as **incrementar automaticamente a revisão com cada versão** caixa de seleção.  
  
## <a name="see-also"></a>Consulte também  
 [Como: Definir a publicação do ClickOnce versão](../deployment/how-to-set-the-clickonce-publish-version.md)   
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como: Publicar um aplicativo ClickOnce usando o assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
