---
title: 'Como: Alterar o idioma de publicação para um aplicativo ClickOnce | Microsoft Docs'
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
ms.openlocfilehash: 2a50beda49895396bf9fec48213836a109d8a873
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442176"
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>Como: Alterar o idioma de publicação de um aplicativo ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao publicar um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo, a interface do usuário exibida durante a instalação padrão é o idioma e cultura do computador de desenvolvimento. Se você estiver publicando um aplicativo localizado, você precisará especificar um idioma e cultura para coincidir com a versão localizada. Isso é determinado pelo `Publish language` propriedade para o seu projeto.  
  
 O `Publish language` propriedade pode ser definida **opções de publicação** caixa de diálogo, acessível a partir o **publicar** página do **Designer de projeto**.  
  
> [!NOTE]
> As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-change-the-publish-language"></a>Para alterar o idioma de publicação  
  
1. Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2. Clique o **publicar** guia.  
  
3. Clique o **opções** para abrir o **opções de publicação** caixa de diálogo.  
  
4. Clique em **descrição**.  
  
5. No **opções de publicação** diálogo caixa, selecione um idioma e cultura da **linguagem de publicação** lista suspensa e clique **Okey**.  
  
## <a name="see-also"></a>Consulte também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como: Publicar um aplicativo ClickOnce usando o assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
