---
title: Ler modelos e diagramas em outras edições do Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
ms.assetid: 46eee279-a9e4-4742-a024-5bd2cf032b86
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a6a7c944eb3d5378ad0fc1542b90ad182f7eb976
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671288"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Ler modelos e diagramas em outras edições do Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando você abre um modelo em uma versão do Visual Studio que não dá suporte à criação de modelo, o modelo é aberto no modo somente leitura. Nesse modo, você pode alterar o layout dos diagramas, mas não pode alterar o modelo.

 Para ver quais versões do Visual Studio oferecem suporte à criação de modelo, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="obtaining-access-to-a-model-and-diagrams"></a>Obtendo acesso a um modelo e diagramas
 Para ler um diagrama UML ou um diagrama de camada, você deve primeiro usar o Visual Studio para abrir o projeto de modelagem e, em seguida, abrir o diagrama dentro dele.

 Por esse motivo, se você quiser ler um diagrama ou diagrama de camada UML, também deverá ter acesso ao projeto de modelagem no qual ele foi criado. Você pode fazer isso acessando o projeto de [!INCLUDE[esprscc](../includes/esprscc-md.md)] ou obtendo uma cópia dos arquivos de projeto.

> [!NOTE]
> Isso não se aplica a mapas de código e diagramas de classe .NET gerados a partir do código. Esses diagramas podem ser exibidos independentemente de um projeto de modelagem.

 Para ler um diagrama UML ou um diagrama de camada, o conjunto mínimo de arquivos de que você precisa é o seguinte:

- Os dois arquivos de diagrama do diagrama que você deseja ler, por exemplo, **MyDiagram. classdiagram e MyDiagram. classdiagram. layout**.

    > [!NOTE]
    > Para diagramas de camada, você também deve ter o arquivo chamado _MyDiagram_ **. layerdiagram. supressões**.

- O arquivo de projeto de modelagem (**MyModel. modelproj**)

- O arquivo de modelo raiz (**ModelDefinition\MyModel.Uml**)

- Os arquivos de pacote para qualquer pacote referenciado no diagrama (**ModelDefinition\MyPackage.Uml**)

## <a name="changes-that-you-can-make-in-read-only-mode"></a>Alterações que você pode fazer no modo somente leitura
 Se você abrir um modelo e seus diagramas em uma versão do Visual Studio que não ofereça suporte à criação de modelo, não será possível alterar o modelo. Ou seja, você não pode alterar os elementos e as relações que são exibidos nos diagramas ou no Gerenciador de modelos. No entanto, você pode fazer algumas alterações no layout dos diagramas:

- Reorganize as formas e os conectores no diagrama.

- Expandir e recolher formas.

  Você pode salvar essas alterações. Se você quiser tornar as alterações visíveis para outros usuários, será necessário pelo menos enviar os arquivos **. layout** atualizados.

## <a name="RelatedTopics"></a> Tópicos relacionados

|Título|Descrição|
|-----------|-----------------|
|[Diagramas de camada: referência](../modeling/layer-diagrams-reference.md)|Um diagrama de camada mostra a estrutura de uma arquitetura existente ou proposta. Quando o código é escrito, ele pode ser validado automaticamente em um diagrama de camada.|
|[Diagramas de atividade UML: referência](../modeling/uml-activity-diagrams-reference.md)|Um diagrama de atividade mostra um fluxo de trabalho, seja em um processo comercial ou em software.|
|[Diagramas de classe UML: referência](../modeling/uml-class-diagrams-reference.md)|Um diagrama de classe mostra tipos e relações usados em muitos contextos, como código, esquemas de banco de dados, protocolos de comunicação ou o Glossário de termos usados para descrever um domínio de negócios.|
|[Diagramas de componente UML: referência](../modeling/uml-component-diagrams-reference.md)|Um diagrama de componente mostra partes separáveis em um design de software e suas interfaces.|
|[Diagramas de sequência UML: referência](../modeling/uml-sequence-diagrams-reference.md)|Um diagrama de sequência mostra as interações entre os elementos em um design de software.|
|[Diagramas de caso de uso UML: referência](../modeling/uml-use-case-diagrams-reference.md)|Um diagrama de caso de uso mostra os usuários de um sistema e as atividades que eles podem executar para obter metas específicas.|

## <a name="see-also"></a>Consulte também
 [Criar modelos para o aplicativo](../modeling/create-models-for-your-app.md)
