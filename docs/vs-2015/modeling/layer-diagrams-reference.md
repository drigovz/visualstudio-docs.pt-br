---
title: 'Diagramas de camada: referência | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.layerdiagram.layerexplorer.artifactlink
- vs.teamarch.layerdiagram.layerexplorer.artifactlink.properties
- vs.teamarch.layerdiagram.diagram
- vs.teamarch.UMLModelExplorer.layerdiagram
- vs.teamarch.layerdiagram.layerexplorer
- vs.teamarch.layerdiagram.shapes.properties
- vs.teamarch.layerdiagram.toolbox
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: f26c986c-1e79-420e-b29a-a283e6d8a71d
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a8a0654936ac102891981ecbee43430172487628
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646118"
---
# <a name="layer-diagrams-reference"></a>Diagramas de camada: referência
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No Visual Studio, você pode usar um *diagrama de camada* para visualizar a arquitetura lógica de alto nível do seu sistema. Um diagrama de camada organiza os artefatos físicos em seu sistema em grupos lógicos e abstratos chamados *camadas*. Essas camadas descrevem as principais tarefas que os artefatos executam ou os principais componentes do seu sistema. Cada camada também pode conter camadas aninhadas que descrevem tarefas mais detalhadas.

 Para ver quais versões do Visual Studio oferecem suporte a esse recurso, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Você pode especificar as dependências pretendidas ou existentes entre camadas. Essas dependências, que são representadas como setas, indicam quais camadas podem usar ou usar atualmente a funcionalidade representada por outras camadas. Ao organizar seu sistema em camadas que descrevem funções e funções distintas, um diagrama de camada pode ajudar a facilitar a compreensão, a reutilização e a manutenção de seu código.

 Use um diagrama de camada para ajudá-lo a executar as seguintes tarefas:

- Comunique a arquitetura lógica existente ou pretendida do seu sistema.

- Descubra conflitos entre o código existente e a arquitetura pretendida.

- Visualize o impacto das alterações na arquitetura pretendida ao refatorar, atualizar ou desenvolver seu sistema.

- Reforce a arquitetura pretendida durante o desenvolvimento e a manutenção do seu código, incluindo a validação com o check-in e as operações de compilação.

  Este tópico descreve os elementos que você pode usar em um diagrama de camada. Para obter informações mais detalhadas sobre como criar e desenhar diagramas de camada, consulte [diagramas de camada: diretrizes](../modeling/layer-diagrams-guidelines.md). Para obter mais informações sobre padrões de camadas, visite o [site patterns & Practices](http://go.microsoft.com/fwlink/?LinkId=145794).

## <a name="reading-layer-diagrams"></a>Lendo diagramas de camada
 ![Elementos em diagramas de camada](../modeling/media/uml-layerrefreading.png "UML_LayerRefReading")

 A tabela a seguir descreve os elementos que você pode usar em um diagrama de camada.

|**La**|**Elemento**|**Descrição**|
|---------------|-----------------|---------------------|
|1|**Camada**|Um grupo lógico de artefatos físicos em seu sistema. Esses artefatos podem ser namespaces, projetos, classes, métodos e assim por diante.<br /><br /> Para ver os artefatos que estão vinculados a uma camada, abra o menu de atalho da camada e escolha **exibir links** para abrir o **Gerenciador de camadas**.<br /><br /> Para obter mais informações, consulte [Gerenciador de camadas](#Explorer).<br /><br /> **dependências de namespace proibidas** -   -especifica que os artefatos associados a essa camada não podem depender dos namespaces especificados.<br />-    de**namespaces proibidos** – especifica que os artefatos associados a essa camada não devem pertencer aos namespaces especificados.<br />-   **namespaces necessários** -especifica que os artefatos associados a essa camada devem pertencer a um dos namespaces especificados.|
|2|**Estados**|Indica que uma camada pode usar a funcionalidade em outra camada, mas não vice-versa.<br /><br /> **direção** de -   -especifica a direção da dependência.|
|3|**Dependência bidirecional**|Indica que uma camada pode usar a funcionalidade em outra camada e vice-versa.<br /><br /> **direção** de -   -especifica a direção da dependência.|
|4|**Comentário**|Use para adicionar notas gerais ao diagrama ou aos elementos no diagrama.|
|5|**Link de comentário**|Use para vincular comentários a elementos no diagrama.|

## <a name="Explorer"></a>Gerenciador de camadas
 Você pode vincular cada camada a artefatos em sua solução, como projetos, classes, namespaces, arquivos de projeto e outras partes do seu software. O número em uma camada mostra o número de artefatos vinculados à camada. No entanto, ao ler o número de artefatos em uma camada, lembre-se do seguinte:

- Se uma camada estiver vinculada a um artefato que contenha outros artefatos, mas não estiver vinculada diretamente a outros artefatos, o número incluirá apenas o artefato vinculado. No entanto, os outros artefatos estão incluídos para análise durante a validação da camada.

   Por exemplo, se uma camada estiver vinculada a um único namespace, o número de artefatos vinculados será 1, mesmo se o namespace contiver classes. Se a camada também tiver links para cada classe no namespace, o número incluirá as classes vinculadas.

- Se uma camada contiver outras camadas vinculadas a artefatos, a camada de contêiner também estará vinculada a esses artefatos, mesmo que o número na camada de contêiner não inclua esses artefatos.

  Para obter mais informações sobre como vincular camadas e artefatos, consulte:

- [Diagramas de camada: diretrizes](../modeling/layer-diagrams-guidelines.md)

- [Criar diagramas de camada por meio de código](../modeling/create-layer-diagrams-from-your-code.md)

#### <a name="to-examine-the-linked-artifacts"></a>Para examinar os artefatos vinculados

- No diagrama de camada, abra o menu de atalho para uma ou mais camadas e escolha **exibir links**.

     O **Gerenciador de camadas** é aberto e mostra os artefatos que estão vinculados às camadas selecionadas. O **Gerenciador de camadas** tem uma coluna que mostra cada uma das propriedades dos links de artefato.

    > [!NOTE]
    > Se você não puder ver todas essas propriedades, expanda a janela **Gerenciador de camadas** .

    |**Coluna no Gerenciador de camadas**|**Descrição**|
    |----------------------------------|---------------------|
    |**Às**|O tipo de artefato, como uma classe, um namespace, um arquivo de origem e assim por diante|
    |**Camada**|A camada que vincula ao artefato|
    |**Dá suporte à validação**|Se **for true**, o processo de validação de camada poderá verificar se o projeto está de acordo com as dependências de ou para esse elemento.<br /><br /> Se **for false**, o link não participará do processo de validação de camada.<br /><br /> Para obter mais informações, consulte [diagramas de camada: diretrizes](../modeling/layer-diagrams-guidelines.md).|
    |**Identificador**|A referência ao artefato vinculado|

## <a name="see-also"></a>Consulte também
 [Criar modelos para o aplicativo](../modeling/create-models-for-your-app.md)
