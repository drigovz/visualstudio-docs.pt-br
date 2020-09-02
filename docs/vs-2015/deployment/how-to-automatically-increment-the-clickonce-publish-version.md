---
title: 'Como: incrementar automaticamente a versão de publicação do ClickOnce | Microsoft Docs'
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
ms.openlocfilehash: 50faf70e8eda6ef7ab01201102540729497eb87b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683916"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Como incrementar a versão da publicação do ClickOnce automaticamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao publicar um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo, alterar a `Publish Version` propriedade faz com que o aplicativo seja publicado como uma atualização. Por padrão, o Visual Studio incrementa automaticamente o `Revision` número de `Publish Version` cada vez que você publica o aplicativo.  
  
 Você pode desabilitar esse comportamento na página **publicar** do designer de **projeto**.  
  
> [!NOTE]
> As caixas de diálogo e os comandos de menu encontrados podem diferir daqueles descritos na Ajuda, dependendo das configurações ativas ou edição. Para alterar suas configurações, selecione **Importar e Exportar Configurações** no menu **Ferramentas** . Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-disable-automatically-incrementing-the-publish-version"></a>Para desabilitar o incrementamento automático da versão de publicação  
  
1. Com um projeto selecionado no **Gerenciador de soluções**, no menu **projeto** , clique em **Propriedades**.  
  
2. Clique na guia **Publicar**.  
  
3. Na seção **Publicar versão** , desmarque a caixa de seleção **incrementar revisão automaticamente com cada versão** .  
  
## <a name="see-also"></a>Consulte Também  
 [Como: definir a versão de publicação do ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)   
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como publicar um Aplicativo ClickOnce usando o Assistente de Publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
