---
title: Depurar aplicativo ClickOnce com permissões restritas
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0d942c41aac873b775566efa4e128651a8830e92
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727960"
---
# <a name="how-to-debug-a-clickonce-application-with-restricted-permissions"></a>Como depurar um aplicativo ClickOnce com permissões restritas
Como desenvolvedor, você provavelmente está executando seu computador de desenvolvimento com permissões de confiança total, portanto, você não verá as mesmas exceções de segurança ao depurar um aplicativo ClickOnce que o usuário final pode ver ao executá-lo com permissões restritas.

 Para capturar essas exceções, você precisa depurar o aplicativo com as mesmas permissões que o usuário final. A depuração com permissões restritas pode ser habilitada na página **segurança** do **Designer de projeto**.

 Além disso, quando você desenvolve aplicativos que chamam serviços da Web, esses serviços da Web geralmente residem em seu computador de desenvolvimento. Depois de implantado, o usuário final acessará esses serviços Web de uma URL diferente. Para emular a experiência do usuário final durante a depuração, você pode especificar uma URL e o depurador tratará os serviços Web como se estivessem sendo chamados a partir dessa URL.

### <a name="to-enable-debugging-with-restricted-permissions"></a>Para habilitar a depuração com permissões restritas

1. Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.

2. No **Designer de projeto**, clique na guia **segurança** .

3. Marque a caixa de seleção **Habilitar configuração de segurança do ClickOnce** e, em seguida, clique no botão **esta opção é um aplicativo de confiança parcial** .

4. Clique no botão **Avançado**.

5. Marque a caixa de seleção **depurar este aplicativo com o conjunto de permissões selecionado** e clique em **OK**.

     Quando você depura o aplicativo, qualquer tentativa de acessar uma permissão que não faça parte do conjunto de permissões gerará uma exceção de segurança.

### <a name="to-specify-a-url-for-debugging"></a>Para especificar uma URL para depuração

1. Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.

2. No **Designer de projeto**, clique na guia **segurança** .

3. Marque a caixa de seleção **Habilitar configuração de segurança do ClickOnce** e, em seguida, clique no botão **esta opção é um aplicativo de confiança parcial** .

4. Clique no botão **Avançado**.

5. Marque a caixa de seleção **depurar este aplicativo com o conjunto de permissões selecionado** e clique em **OK**.

6. Na caixa de texto **depurar este aplicativo como se ele fosse baixado da seguinte URL** , insira uma URL ou um caminho de rede.

## <a name="see-also"></a>Consulte também
- [Como definir permissões personalizadas para um aplicativo ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Proteger aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)
- [Segurança de acesso do código para aplicativos ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
- [Proteger aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)