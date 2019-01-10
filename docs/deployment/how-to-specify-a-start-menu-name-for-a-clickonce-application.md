---
title: 'Como: Especifique um nome no Menu Iniciar para um aplicativo ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eeee762f8bf4ce8df9744e6e39d1f0bd4345cb10
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947810"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Como: Especificar um nome no menu Iniciar para um aplicativo ClickOnce
Quando um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo é instalado para uso online e offline, uma entrada é adicionada para o **começar** menu e o **adicionar ou remover programas** lista. Por padrão, o nome de exibição é o mesmo que o nome do assembly do aplicativo, mas você pode alterar o nome de exibição, definindo **nome do produto** na **opções de publicação** caixa de diálogo.  
  
 **Nome do produto** será exibida na *Publish. htm* página; para um aplicativo offline instalado, ele será o nome da entrada no **iniciar** menu e ele também será o nome que aparece no **Adicionar ou remover programas**.  
  
 **Nome do publicador** será exibido na *Publish. htm* página acima **nome do produto**, e para um aplicativo offline instalado, ele também será o nome da pasta que contém o aplicativo ícone na **iniciar** menu.  

 A referência de início menu de atalho ou aplicativo é criada no *%appdata%\Microsoft\Windows\Start Iniciar\Programas\\< nome do publicador\>*. A referência de atalho ou o aplicativo tem o mesmo nome que o nome do produto.
  
 Você pode definir as **nome do produto** e **nome do publicador** propriedades no **opções de publicação** caixa de diálogo, disponível no **publicar** página dos **Designer de projeto**.  
  
### <a name="to-specify-a-start-menu-name"></a>Para especificar um nome no menu Iniciar  
  
1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2.  Clique o **publicar** guia.  
  
3.  Clique o **opções** para abrir o **opções de publicação** caixa de diálogo.  
  
4.  Clique em **descrição**.  
  
5.  No **opções de publicação** caixa de diálogo, digite o nome a ser exibido no **nome do produto**.  
  
6.  Opcionalmente, você pode inserir um nome de editor no **nome do publicador**.  
  
## <a name="see-also"></a>Consulte também  
 [Publicar aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como: Publicar um aplicativo ClickOnce usando o assistente de publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)