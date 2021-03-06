---
title: Como fazer para atribuir assinaturas do Visual Studio?
description: Você pode atribuir assinaturas aos usuários finais uma de cada vez ou usando o recurso Adição em massa para carregar de maneira rápida e fácil um número maior...
ms.faqid: group1_3
ms.topic: include
ms.assetid: 59eb35fd-ec94-41ce-b24c-a8a120976bac
author: CaityBuschlen
ms.author: cabuschl
ms.date: 12/03/2020
ms.openlocfilehash: 5a12d59f90ee2a09002efcb99c78cfd563060006
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96584509"
---
## <a name="how-do-i-assign-visual-studio-subscriptions"></a>Como fazer para atribuir assinaturas do Visual Studio?

Você pode atribuir assinaturas aos usuários finais uma de cada vez ou usando o recurso Adição em massa para carregar de maneira rápida e fácil um número maior de assinantes de cada vez.

Para atribuir assinaturas individualmente:

1. Selecione a [guia Gerenciar Assinantes](https://manage.visualstudio.com/subscribers) na parte superior da página em [manage.visualstudio.com](https://manage.visualstudio.com)
2. Selecione Adicionar e digite o nome e o endereço de email do usuário ao qual você deseja atribuir uma assinatura.
    1. Caso sua organização esteja usando o Azure Active Directory, o campo de nome faz uma pesquisa para encontrar pessoas no seu diretório atual. Selecione uma delas nos resultados da pesquisa ou adicione alguém manualmente.
3. Caso deseje que esse assinante tenha acesso aos downloads de software quando ele entrar no [Portal de Assinaturas do Visual Studio](https://my.visualstudio.com/), mantenha a alternância de downloads habilitada na seção Configurações de download.
4. Preencha a seção Opções de Comunicação para nos informar do idioma em que devemos enviar o email de atribuição de assinantes.
5. Caso deseje adicionar alguma anotação associada à atribuição, use a seleção Referência.
6. Selecione Adicionar na parte inferior do painel do submenu para concluir a atribuição de assinatura. O assinante receberá um email e poderá começar a usar a assinatura do Visual Studio imediatamente (nenhuma ativação é necessária por parte do assinante).

Para atribuir assinaturas em massa:

1. Selecione a [guia Gerenciar Assinantes](https://manage.visualstudio.com/subscribers) na parte superior da página em [manage.visualstudio.com](https://manage.visualstudio.com).
2. Selecione Adição em massa, baixe o modelo do Excel e salve uma cópia local.
3. Todos os campos são obrigatórios, com exceção do campo Referência.
    1. Verifique se nenhum dos campos do formulário contém vírgulas.
    2. Remova os espaços antes e depois de campos de formulário.
    3. Verifique se os nomes não contêm espaços extras entre nomes ou sobrenomes de duas partes (por exemplo, se uma pessoa tiver um nome de duas partes, como 'Maria Eduarda', ele deverá ser digitado como 'MariaEduarda').
4. Volte a [manage.visualstudio.com](https://manage.visualstudio.com), selecione Adição em massa e carregue a cópia salva do modelo do Excel.
5. Quando o upload for bem-sucedido, você verá uma página de confirmação e a lista de assinantes preenchida com os novos assinantes. Os assinantes receberão um email e poderão começar a usar a respectiva assinatura do Visual Studio imediatamente (nenhuma ativação é necessária por parte do assinante).

Para saber mais sobre como atribuir assinaturas de maneira rápida e fácil, [leia mais informações](https://docs.microsoft.com/visualstudio/subscriptions/assign-license#add-a-single-subscriber) no portal do Administrador de Assinaturas do Visual Studio.  [Saiba mais](https://docs.microsoft.com/visualstudio/subscriptions/assign-github) sobre como gerenciar assinaturas do Visual Studio com o GitHub Enterprise. 

## <a name="what-is-the-github-enterprise-setup-process"></a>O que é o processo de configuração do GitHub Enterprise? 

O GitHub Enterprise é configurado e gerenciado separadamente das assinaturas do Visual Studio. Após uma assinatura do Visual Studio com a compra do GitHub Enterprise, um processo de configuração de conta do GitHub Enterprise é iniciado paralelamente (mas em separado) ao estabelecimento de um contrato no manage.visualstudio.com. O estabelecimento dessa conta do GitHub Enterprise pode demorar um pouco.  

Depois que sua empresa tiver configurado uma conta do GitHub Enterprise, os assinantes atribuídos com assinaturas do Visual Studio com o GitHub Enterprise receberão um email do GitHub notificando-os sobre a vinculação de suas assinaturas do Visual Studio. Depois que os assinantes receberem esse email, poderão entrar em contato com o administrador da organização do GitHub para serem convidados para a organização apropriada. 

[Leia mais](https://docs.microsoft.com/visualstudio/subscriptions/assign-github) sobre como gerenciar assinaturas do Visual Studio com o GitHub Enterprise. Consulte a [documentação do assinante](https://docs.microsoft.com/visualstudio/subscriptions/access-github) para saber mais detalhes sobre o processo de configuração do GitHub Enterprise. 