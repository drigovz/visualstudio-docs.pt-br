---
title: 'Como: Depurar um aplicativo ClickOnce com permissões restritas | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], ClickOnce applications
- ClickOnce deployment, debugging
- ClickOnce applications, debugging
ms.assetid: 6991ea91-5253-451b-923d-22273a3d38b1
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d60f88c4d1532a03922f12f21bb9b455ef5d84d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153795"
---
# <a name="how-to-debug-a-clickonce-application-with-restricted-permissions"></a>Como depurar um aplicativo ClickOnce com permissões restritas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Como desenvolvedor, você provavelmente está executando seu computador de desenvolvimento com permissões de confiança total, portanto, você não verá as mesmas exceções de segurança ao depurar um aplicativo ClickOnce que o usuário final pode ver ao executá-lo com permissões restritas.  
  
 Para capturar essas exceções, você precisa depurar o aplicativo com as mesmas permissões que o usuário final. A depuração com permissões restritas pode ser habilitada na página **segurança** do **Designer de projeto**.  
  
 Além disso, quando você desenvolve aplicativos que chamam serviços da Web, esses serviços da Web geralmente residem em seu computador de desenvolvimento. Depois de implantado, o usuário final acessará esses serviços Web de uma URL diferente. Para emular a experiência do usuário final durante a depuração, você pode especificar uma URL e o depurador tratará os serviços Web como se estivessem sendo chamados a partir dessa URL.  
  
### <a name="to-enable-debugging-with-restricted-permissions"></a>Para habilitar a depuração com permissões restritas  
  
1. Com um projeto selecionado no **Gerenciador de soluções**, no menu **projeto** , clique em **Propriedades**.  
  
2. No **Designer de projeto**, clique na guia **segurança** .  
  
3. Marque a caixa de seleção **Habilitar configuração de segurança do ClickOnce** e, em seguida, clique no botão **esta opção é um aplicativo de confiança parcial** .  
  
4. Clique no botão **Avançado** .  
  
5. Marque a caixa de seleção **depurar este aplicativo com o conjunto de permissões selecionado** e clique em **OK**.  
  
     Quando você depura o aplicativo, qualquer tentativa de acessar uma permissão que não faça parte do conjunto de permissões gerará uma exceção de segurança.  
  
### <a name="to-specify-a-url-for-debugging"></a>Para especificar uma URL para depuração  
  
1. Com um projeto selecionado no **Gerenciador de soluções**, no menu **projeto** , clique em **Propriedades**.  
  
2. No **Designer de projeto**, clique na guia **segurança** .  
  
3. Marque a caixa de seleção **Habilitar configuração de segurança do ClickOnce** e, em seguida, clique no botão **esta opção é um aplicativo de confiança parcial** .  
  
4. Clique no botão **Avançado** .  
  
5. Marque a caixa de seleção **depurar este aplicativo com o conjunto de permissões selecionado** e clique em **OK**.  
  
6. Na caixa de texto **depurar este aplicativo como se ele fosse baixado da seguinte URL** , insira uma URL ou um caminho de rede.  
  
## <a name="see-also"></a>Consulte Também  
 [Como: definir permissões personalizadas para um aplicativo ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Segurança de acesso do código para aplicativos ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)
