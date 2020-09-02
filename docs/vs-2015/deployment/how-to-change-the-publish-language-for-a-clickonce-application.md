---
title: 'Como: alterar o idioma de publicação para um aplicativo ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish language property
- ClickOnce deployment, changing publish language
- publishing, ClickOnce
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 26e4074b731dad44cd9eed40f1c1cc755d786562
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683807"
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>Como alterar o idioma de publicação para um aplicativo ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao publicar um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo, a interface do usuário exibida durante a instalação usa como padrão o idioma e a cultura do seu computador de desenvolvimento. Se você estiver publicando um aplicativo localizado, será necessário especificar um idioma e uma cultura para corresponder à versão localizada. Isso é determinado pela `Publish language` Propriedade do seu projeto.  
  
 A `Publish language` propriedade pode ser definida na caixa de diálogo **Opções de publicação** , acessível na página **publicar** do **Designer de projeto**.  
  
> [!NOTE]
> As caixas de diálogo e os comandos de menu encontrados podem diferir daqueles descritos na Ajuda, dependendo das configurações ativas ou edição. Para alterar suas configurações, selecione **Importar e Exportar Configurações** no menu **Ferramentas** . Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-change-the-publish-language"></a>Para alterar a linguagem de publicação  
  
1. Com um projeto selecionado no **Gerenciador de soluções**, no menu **projeto** , clique em **Propriedades**.  
  
2. Clique na guia **Publicar**.  
  
3. Clique no botão **Opções** para abrir a caixa de diálogo **Opções de publicação** .  
  
4. Clique em **Descrição**.  
  
5. Na caixa de diálogo **Opções de publicação** , selecione um idioma e uma cultura na lista suspensa **idioma de publicação** e clique em **OK**.  
  
## <a name="see-also"></a>Consulte Também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como publicar um Aplicativo ClickOnce usando o Assistente de Publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
