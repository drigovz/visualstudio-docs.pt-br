---
title: Visão geral de aplicativos de dados de N camadas | Microsoft Docs
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
- presentation tier
- middle tier
- data tier
- n-tier applications, about n-tier applications
ms.assetid: 1020581d-eaaa-41a2-aca4-bf4c212895f6
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0f124e997669370e71819cf37423d0c2d6a414d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658064"
---
# <a name="n-tier-data-applications-overview"></a>Visão geral de aplicativos de dados de N camadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os aplicativos de dados de N camadas * são aplicativos de dados separados em várias *camadas*. Também chamados de "aplicativos distribuídos" e "aplicativos multicamadas", os aplicativos de n camadas separam o processamento em camadas discretas que são distribuídas entre o cliente e o servidor. Ao desenvolver aplicativos que acessam dados, você deve ter uma separação clara entre as várias camadas que compõem o aplicativo.

 Um aplicativo de n camadas típico inclui uma camada de apresentação, uma camada intermediária e uma camada de dados. A maneira mais fácil de separar as várias camadas em um aplicativo de n camadas é criar projetos discretos para cada camada que você deseja incluir em seu aplicativo. Por exemplo, a camada de apresentação pode ser um aplicativo Windows Forms, enquanto a lógica de acesso a dados pode ser uma biblioteca de classes localizada na camada intermediária. Além disso, a camada de apresentação pode se comunicar com a lógica de acesso de dados na camada intermediária por meio de um serviço, como um serviço. Dividir componentes do aplicativo em camadas separadas aumenta a facilidade de manutenção e a escalabilidade do aplicativo. Ele faz isso habilitando a adoção mais fácil de novas tecnologias que podem ser aplicadas a uma única camada sem a necessidade de reprojetar a solução inteira. Além disso, os aplicativos de n camadas normalmente armazenam informações confidenciais na camada intermediária, o que mantém o isolamento da camada de apresentação.

 O Visual Studio contém vários recursos para ajudar os desenvolvedores a criar aplicativos de n camadas:

- O designer de conjunto de dados fornece uma propriedade de **projeto de conjunto** de dados que permite que você separe o DataSet (camada de entidade de dado) e `TableAdapter` s (camada de acesso a data) em projetos discretos.

- As [ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) fornecem configurações para gerar o DataContext e as classes de dados em namespaces separados. Isso permite a separação lógica das camadas de acesso a dados e de entidade de dados.

- [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) fornece o <xref:System.Data.Linq.Table%601.Attach%2A> método que permite reunir o DataContext de diferentes camadas em um aplicativo. Para obter mais informações, consulte [N camadas e aplicativos remotos com LINQ to SQL](https://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598).

## <a name="presentation-tier"></a>Camada de apresentação
 A *camada de apresentação* é a camada na qual os usuários interagem com um aplicativo. Ele geralmente também contém lógica adicional do aplicativo. Os componentes típicos da camada de apresentação incluem o seguinte:

- Componentes de vinculação de dados, como o <xref:System.Windows.Forms.BindingSource> e o <xref:System.Windows.Forms.BindingNavigator> .

- Representações de objeto de dados, como [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) classes de entidade para uso na camada de apresentação.

  A camada de apresentação normalmente acessa a camada intermediária usando uma referência de serviço (por exemplo, um [Windows Communication Foundation serviços e WCF Data Services no aplicativo do Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) ). A camada de apresentação não acessa diretamente a camada de dados. A camada de apresentação se comunica com a camada de dados por meio do componente de acesso a dados na camada intermediária.

## <a name="middle-tier"></a>Camada Intermediária
 A camada *intermediária* é a camada que a camada de apresentação e a camada de dados usam para se comunicar entre si. Os componentes típicos da camada intermediária incluem o seguinte:

- Lógica de negócios, como regras de negócio e validação de dados.

- Componentes de acesso a dados e lógica, como o seguinte:

  - [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) e [dataadaptadores e datalêrs](https://msdn.microsoft.com/library/cc952ca2-ec19-46ab-9189-15174b52cb74).

  - Representações de objeto de dados, como [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) classes de entidade.

  - Serviços de aplicativos comuns, como autenticação, autorização e personalização.

  A ilustração a seguir mostra os recursos e as tecnologias disponíveis no Visual Studio e onde eles podem se ajustar à camada intermediária de um aplicativo de n camadas.

  ![Componentes da camada intermediária](../data-tools/media/ntiermid.png "NtierMid") Camada intermediária

  A camada intermediária normalmente se conecta à camada de dados usando uma conexão de dados. Essa conexão de dados normalmente é armazenada no componente de acesso a dados.

## <a name="data-tier"></a>Camada de Dados
 A *camada de dados* é basicamente o servidor que armazena os dados de um aplicativo (por exemplo, um servidor que executa o [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ).

 A ilustração a seguir mostra os recursos e as tecnologias disponíveis no Visual Studio e onde eles podem se ajustar à camada de dados de um aplicativo de n camadas.

 ![Componentes da camada de dados](../data-tools/media/ntierdatatier.png "ntierdatatier") Camada de dados

 A camada de dados não pode ser acessada diretamente do cliente na camada de apresentação. Em vez disso, o componente de acesso a dados na camada intermediária é usado para comunicação entre as camadas de apresentação e de dados.

## <a name="help-for-n-tier-development"></a>Ajuda para o desenvolvimento de N camadas
 Os tópicos a seguir fornecem informações sobre como trabalhar com aplicativos de n camadas:

 [Separar conjuntos de dados e TableAdapters em diferentes projetos](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)

 [Passo a passo: criando um aplicativo de dados de N camadas](../data-tools/walkthrough-creating-an-n-tier-data-application.md)

 [Instruções passo a passo: adicionando validação a um aplicativo de dados de N camadas](https://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265)

 [Aplicativos de n camadas e remoto com LINQ to SQL](https://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)

## <a name="see-also"></a>Consulte Também
 <xref:System.Data.Linq.ITable.Attach%2A>[Walkthrough: Criando um](../data-tools/walkthrough-creating-an-n-tier-data-application.md) conjunto de dados de [atualização hierárquica](../data-tools/hierarchical-update.md) de aplicativos de data de N camadas [no Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) [acessando dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
