---
title: 'Como: Adicionar, atualizar ou remover uma referência do WCF Data Service | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 89a667e3254be8161d4defb54d524756a5eb02fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670013"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Como adicionar, atualizar ou remover uma referência de WCF Data Services
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uma *referência de serviço* permite que um projeto acesse um ou mais [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] . Use a caixa de diálogo **Adicionar referência de serviço** para procurar [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] na solução atual, localmente, em uma rede local ou na Internet.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="adding-a-service-reference"></a>Adicionando uma referência de serviço

#### <a name="to-add-a-reference-to-an-external-service"></a>Para adicionar uma referência a um serviço externo

1. No **Gerenciador de soluções**, clique com o botão direito do mouse no nome do projeto ao qual você deseja adicionar o serviço e, em seguida, clique em **Adicionar referência de serviço**.

     A caixa de diálogo **Adicionar Referência de Serviço** é exibida.

2. Na caixa **endereço** , insira a URL para o serviço e clique em **ir** para pesquisar o serviço. Se o serviço implementa a segurança de nome de usuário e senha, você pode ser solicitado a fornecer um nome de usuário e senha.

    > [!NOTE]
    > Você só deve fazer referência a serviços de uma fonte confiável. A adição de referências de uma fonte não confiável pode comprometer a segurança.

     Você também pode selecionar a URL na lista de **endereços** , que armazena as 15 URLs anteriores nas quais os metadados de serviço válidos foram encontrados.

     Uma barra de progresso é exibida quando a pesquisa está sendo executada. Você pode interromper a pesquisa a qualquer momento clicando em **parar**.

3. Na lista de **Serviços** , expanda o nó do serviço que você deseja usar e selecione um conjunto de entidades.

4. Na caixa **Namespace**, digite o namespace que deseja usar para a referência.

5. Clique em **OK** para adicionar a referência ao projeto.

     Um cliente de serviço (proxy) é gerado e os metadados que descrevem o serviço são adicionados ao arquivo de app.config.

#### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Para adicionar uma referência a um serviço na solução atual

1. No **Gerenciador de soluções**, clique com o botão direito do mouse no nome do projeto ao qual você deseja adicionar o serviço e, em seguida, clique em **Adicionar referência de serviço**.

     A caixa de diálogo **Adicionar Referência de Serviço** é exibida.

2. Clique em **descobrir**.

     Todos os serviços ( [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] e serviços WCF) na solução atual são adicionados à lista de **Serviços** .

3. Na lista de **Serviços** , expanda o nó do serviço que você deseja usar e selecione um conjunto de entidades.

4. Na caixa **Namespace**, digite o namespace que deseja usar para a referência.

5. Clique em **OK** para adicionar a referência ao projeto.

     Um cliente de serviço (proxy) é gerado e os metadados que descrevem o serviço são adicionados ao arquivo de app.config.

## <a name="updating-a-service-reference"></a>Atualizando uma referência de serviço
 Às vezes, o Modelo de Dados de Entidade para um [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] será alterado. Quando isso acontece, a referência de serviço deve ser atualizada.

#### <a name="to-update-a-service-reference"></a>Para atualizar uma referência de serviço

- Em **Gerenciador de soluções**, clique com o botão direito do mouse na referência de serviço e clique em **Atualizar referência de serviço**.

     Uma caixa de diálogo de progresso é exibida enquanto a referência é atualizada a partir de seu local original e o cliente de serviço é regenerado para refletir as alterações nos metadados.

## <a name="removing-a-service-reference"></a>Removendo uma referência de serviço
 Se uma referência de serviço não estiver mais sendo usada, você poderá removê-la de sua solução.

#### <a name="to-remove-a-service-reference"></a>Para remover uma referência de serviço

- Em **Gerenciador de soluções**, clique com o botão direito do mouse na referência de serviço e clique em **excluir**.

     O cliente de serviço será removido da solução e os metadados que descrevem o serviço serão removidos do arquivo de app.config.

    > [!NOTE]
    > Qualquer código que referencie a referência de serviço precisará ser removido manualmente.

## <a name="see-also"></a>Consulte Também
 [Serviços do Windows Communication Foundation e WCF Data Services no Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
