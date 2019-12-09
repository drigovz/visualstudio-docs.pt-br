---
title: Como adicionar, atualizar ou remover uma referência de WCF Data Services
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- service references [Visual Studio]
- WCF Data Service reference
- WCF data service references
- ADO.NET service references
- ADO.NET Data Service reference
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8f19fbfb82a74de0f0eedf784483ecaeccc9a5fc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648417"
---
# <a name="how-to-add-update-or-remove-a-wcf-data-service-reference"></a>Como adicionar, atualizar ou remover uma referência de serviço de dados do WCF
Uma *referência de serviço* permite que um projeto acesse um ou mais [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]. Use a caixa de diálogo **Adicionar referência de serviço** para procurar [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] na solução atual, localmente, em uma rede local ou na Internet.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-a-service-reference"></a>Adicionar uma referência de serviço

### <a name="to-add-a-reference-to-an-external-service"></a>Para adicionar uma referência a um serviço externo

1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no nome do projeto ao qual você deseja adicionar o serviço e, em seguida, clique em **Adicionar referência de serviço**.

     A caixa de diálogo **Adicionar referência de serviço** é exibida.

2. Na caixa **endereço** , insira a URL para o serviço e clique em **ir** para pesquisar o serviço. Se o serviço implementa a segurança de nome de usuário e senha, você pode ser solicitado a fornecer um nome de usuário e senha.

    > [!NOTE]
    > Você só deve fazer referência a serviços de uma fonte confiável. A adição de referências de uma fonte não confiável pode comprometer a segurança.

     Você também pode selecionar a URL na lista de **endereços** , que armazena as 15 URLs anteriores nas quais os metadados de serviço válidos foram encontrados.

     Uma barra de progresso é exibida quando a pesquisa está sendo executada. Você pode interromper a pesquisa a qualquer momento clicando em **parar**.

3. Na lista de **Serviços** , expanda o nó do serviço que você deseja usar e selecione um conjunto de entidades.

4. Na caixa **namespace** , digite o namespace que você deseja usar para a referência.

5. Clique em **OK** para adicionar a referência ao projeto.

     Um cliente de serviço (proxy) é gerado e os metadados que descrevem o serviço são adicionados ao arquivo *app. config* .

### <a name="to-add-a-reference-to-a-service-in-the-current-solution"></a>Para adicionar uma referência a um serviço na solução atual

1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no nome do projeto ao qual você deseja adicionar o serviço e, em seguida, clique em **Adicionar referência de serviço**.

    A caixa de diálogo **Adicionar referência de serviço** é exibida.

2. Clique em **descobrir**.

    Todos os serviços ([!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] e serviços WCF) na solução atual são adicionados à lista de **Serviços** .

3. Na lista de **Serviços** , expanda o nó do serviço que você deseja usar e selecione um conjunto de entidades.

4. Na caixa **namespace** , digite o namespace que você deseja usar para a referência.

5. Clique em **OK** para adicionar a referência ao projeto.

    Um cliente de serviço (proxy) gera e metadados que descrevem o serviço é adicionado ao arquivo *app. config* .

## <a name="update-a-service-reference"></a>Atualizar uma referência de serviço
Às vezes, o Modelo de Dados de Entidade para uma [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] muda. Quando isso acontece, você deve atualizar a referência de serviço.

### <a name="to-update-a-service-reference"></a>Para atualizar uma referência de serviço

- Em **Gerenciador de soluções**, clique com o botão direito do mouse na referência de serviço e clique em **Atualizar referência de serviço**.

     Uma caixa de diálogo de progresso é exibida enquanto a referência é atualizada a partir de seu local original e o cliente de serviço é regenerado para refletir as alterações nos metadados.

## <a name="remove-a-service-reference"></a>Remover uma referência de serviço
Se uma referência de serviço não estiver mais sendo usada, você poderá removê-la de sua solução.

### <a name="to-remove-a-service-reference"></a>Para remover uma referência de serviço

- Em **Gerenciador de soluções**, clique com o botão direito do mouse na referência de serviço e clique em **excluir**.

     O cliente de serviço será removido da solução e os metadados que descrevem o serviço serão removidos do arquivo *app. config* .

    > [!NOTE]
    > Qualquer código que referencie a referência de serviço deve ser removido manualmente.

## <a name="see-also"></a>Consulte também

- [Serviços do Windows Communication Foundation e WCF Data Services no Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)