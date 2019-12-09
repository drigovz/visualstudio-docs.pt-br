---
title: Como conectar-se a dados em um serviço | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], connecting to Web services
- data sources, creating from Web services
- data [Visual Studio], reading from Web services
- reading data, from Web services
- Web services, reading data
- Web services, as data sources
- Web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9bfa6c776e3a2137f751d4253feb0239811d95a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654698"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Como conectar a dados em um serviço
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Conecte seu aplicativo aos dados retornados de um serviço executando o [Assistente de configuração da fonte de dados](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) e selecionando **serviço** na página **escolher um tipo de fonte de dados** .

 Após a conclusão do assistente, uma referência de serviço é adicionada ao seu projeto e fica imediatamente disponível na [janela fontes de dados](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

> [!NOTE]
> Os itens que aparecem na janela **Fontes de Dados** são dependentes das informações que o serviço retorna. Alguns serviços podem não fornecer informações suficientes para o **Assistente de Configuração de Fonte de Dados** criar objetos associáveis. Por exemplo, se o serviço retornar um conjunto de dados não tipado, nenhum item aparecerá na **janela Data Sources** após a conclusão do assistente. Isso ocorre porque os conjuntos de dados não tipados não fornecem o esquema, portanto, o assistente não tem informações suficientes para criar a fonte de dados.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-connect-your-application-to-a-service"></a>Para conectar seu aplicativo a um serviço

1. No menu **Dados**, clique em **Adicionar Nova Fonte de Dados**.

2. Selecione **serviço** na página **escolher um tipo de fonte de dados** e clique em **Avançar**.

3. Insira o endereço do serviço que você deseja usar ou clique em **descobrir** para localizar os serviços na solução atual e, em seguida, clique em **ir**.

4. Opcionalmente, um novo **namespace** pode ser digitado no lugar do valor padrão.

    > [!NOTE]
    > Clique em **avançado** para abrir a [caixa de diálogo Configurar referência de serviço](../data-tools/configure-service-reference-dialog-box.md).

5. Clique em **OK** para adicionar uma referência de serviço ao seu projeto.

6. Clique em **Finalizar**.

     A fonte de dados é adicionada à janela **fontes de dados** .

## <a name="next-steps"></a>Próximas etapas

#### <a name="to-add-functionality-to-your-application"></a>Para adicionar funcionalidade ao seu aplicativo

- Selecione um item na janela **fontes de dados** e arraste-o para um formulário para criar controles vinculados. Para obter mais informações, confira [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>Consulte também
 [Associar controles WPF a um WCF Data service](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) [Windows Communication Foundation Services e WCF Data Services no Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
