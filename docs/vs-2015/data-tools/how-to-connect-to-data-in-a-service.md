---
title: 'Como: Conectar a dados em um serviço | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e3361ba51607924ee0bd0701f6f2dddf12334f93
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60090375"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Como: Conectar-se a dados em um serviço
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você conecta seu aplicativo para os dados retornados de um serviço executando o [Data Source Configuration Wizard](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) e selecionando **serviço** sobre o **escolher um tipo de fonte de dados**página.  
  
 Após a conclusão do assistente, uma referência de serviço é adicionada ao seu projeto e fica imediatamente disponível na [janela fontes de dados](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
> [!NOTE]
>  Os itens que aparecem na janela **Fontes de Dados** são dependentes das informações que o serviço retorna. Alguns serviços podem não fornecer informações suficientes para o **Assistente de Configuração de Fonte de Dados** criar objetos associáveis. Por exemplo, se o serviço retorna um conjunto de dados não tipado, então nenhum item aparecerá na **janela fontes de dados** após concluir o assistente. Isso ocorre porque os conjuntos de dados não tipados não fornecem esquema, portanto, o assistente não tem informações suficientes para criar a fonte de dados.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-connect-your-application-to-a-service"></a>Conectar seu aplicativo a um serviço  
  
1. No menu **Dados**, clique em **Adicionar Nova Fonte de Dados**.  
  
2. Selecione **serviço** sobre o **escolher um tipo de fonte de dados** página e, em seguida, clique em **próxima**.  
  
3. Insira o endereço do serviço que você deseja usar ou clique em **Discover** para localizar serviços na solução atual e, em seguida, clique em **vá**.  
  
4. Opcionalmente, um novo **Namespace** podem ser digitados no lugar do valor padrão.  
  
    > [!NOTE]
    >  Clique em **Advanced** para abrir o [configurar a caixa de diálogo de referência de serviço](../data-tools/configure-service-reference-dialog-box.md).  
  
5. Clique em **Okey** para adicionar uma referência de serviço ao seu projeto.  
  
6. Clique em **Finalizar**.  
  
     A fonte de dados é adicionada para o **fontes de dados** janela.  
  
## <a name="next-steps"></a>Próximas etapas  
  
#### <a name="to-add-functionality-to-your-application"></a>Para adicionar funcionalidade ao seu aplicativo  
  
- Selecione um item na **fontes de dados** janela e arraste-o para um formulário para criar controles associados. Para obter mais informações, confira [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## <a name="see-also"></a>Consulte também  
 [Associar controles WPF a um WCF data service](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Serviços do Windows Communication Foundation e WCF Data Services no Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
