---
title: 'Diagramas de sequência UML: referência | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.sequencediagram.diagram
- vs.teamarch.UMLModelExplorer.sequencediagram
- vs.teamarch.sequencediagram.toolbox
helpviewer_keywords:
- diagrams - modeling, sequence
- sequence diagrams
- UML diagrams, sequence
- diagrams - modeling, UML sequence
- UML, sequence diagrams
ms.assetid: 366fc324-aeeb-4894-bd13-ec2e40754b8e
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f9b02bbad4fa897404f6c20e12b1705a3ae9ac8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661711"
---
# <a name="uml-sequence-diagrams-reference"></a>Diagramas de sequência UML: referência
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No Visual Studio, um *diagrama de sequência* mostra uma interação, que representa a sequência de mensagens entre instâncias de classes, componentes, subsistemas ou atores. O tempo flui para baixo no diagrama e mostra o fluxo de controle de um participante para outro. Use diagramas de sequência para visualizar instâncias e eventos, em vez de classes e métodos. Mais de uma instância do mesmo tipo pode aparecer no diagrama. Mais de uma ocorrência da mesma mensagem também pode aparecer.

 Os diagramas de sequência UML fazem parte de um modelo UML e existem somente em projetos de modelagem UML. Para criar um diagrama de sequência UML, no menu **arquitetura** , clique em **novo UML ou diagrama de camada**. Saiba mais sobre como criar e desenhar [diagramas de sequência UML](../modeling/uml-sequence-diagrams-guidelines.md) ou [diagramas de modelagem UML](../modeling/edit-uml-models-and-diagrams.md) em geral.

 Para ver quais versões do Visual Studio oferecem suporte a esse recurso, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="reading-sequence-diagrams"></a>Lendo diagramas de sequência
 A tabela a seguir descreve os elementos que você pode ver em um diagrama de sequência. Saiba mais sobre essas [Propriedades de elementos](../modeling/properties-of-elements-on-uml-sequence-diagrams.md).

 ![Partes de um diagrama de sequência](../modeling/media/uml-sequence.png "UML_Sequence")

|**La**|**Elemento**|**Descrição**|
|---------------|-----------------|---------------------|
|1|**Vital**|Uma linha vertical que representa a sequência de eventos que ocorrem em um participante durante uma interação, enquanto o tempo avança na linha. Esse participante pode ser uma instância de uma classe, componente ou ator.|
|2|**Ator**|Um participante que é externo ao sistema que você está desenvolvendo.<br /><br /> Você pode fazer com que um símbolo de ator apareça na parte superior de uma linha da vida definindo sua propriedade de **ator** .|
|3|**Mensagem síncrona**|O remetente aguarda uma resposta a uma mensagem síncrona antes de continuar. O diagrama mostra a chamada e o retorno. As mensagens síncronas são usadas para representar chamadas de função comuns em um programa, bem como outros tipos de mensagem que se comportam da mesma maneira.|
|4|**Mensagem assíncrona**|Uma mensagem que não requer uma resposta antes de o remetente continuar. Uma mensagem assíncrona mostra apenas uma chamada do remetente. Use para representar a comunicação entre threads separados ou a criação de um novo thread.|
|5|**Ocorrência de execução**|Um retângulo sombreado vertical que aparece na linha de vida de um participante e representa o período em que o participante está executando uma operação.<br /><br /> A execução começa onde o participante recebe uma mensagem. Se a mensagem de início era uma mensagem síncrona, a execução termina com uma seta «Return» de volta para o remetente.|
|6|**Mensagem de retorno de chamada**|Uma mensagem que retorna de volta para um participante que está aguardando o retorno de uma chamada anterior. A ocorrência de execução resultante aparece na parte superior da existente.|
|7|**Automensagem**|Uma mensagem de um participante para si mesmo. A ocorrência de execução resultante aparece na parte superior da execução de envio.|
|8|**Criar mensagem**|Uma mensagem que cria um participante. Se um participante receber uma mensagem de criação, ele deverá ser o primeiro que receber.|
|9|**Mensagem encontrada**|Uma mensagem assíncrona de um participante desconhecido ou não especificado.|
|10|**Mensagem perdida**|Uma mensagem assíncrona para um participante desconhecido ou não especificado.|
|11|**Comentário**|Um comentário pode ser anexado a qualquer ponto em uma linha de vida.|
|12|**Uso de interação**|Inclui uma sequência de mensagens que são definidas em outro diagrama.<br /><br /> Para criar um **uso de interação**, clique na ferramenta e arraste entre as linhas de vida que você deseja incluir.|
|13|**Fragmento combinado**|Uma coleção de fragmentos. Cada fragmento pode incluir uma ou mais mensagens. Há diferentes tipos de fragmentos combinados. Para obter mais informações, consulte [descrever o fluxo de controle com fragmentos em diagramas de sequência UML](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md).<br /><br /> Para criar um fragmento, clique com o botão direito do mouse em uma mensagem, aponte para **surround com**e clique em um tipo de fragmento.|
|14|**Proteção de fragmento**|Pode ser usado para declarar uma condição relevante para se o fragmento ocorrerá.<br /><br /> Para definir a proteção, selecione um fragmento e, em seguida, selecione o protetor e digite um valor.|
|**X**|**Evento de destruição**|Representa o ponto no qual o objeto é excluído ou não pode mais ser acessado. Aparece na parte inferior de cada linha da vida.|
||**Inter**|A coleção de mensagens e linhas de vida que são exibidas no diagrama de sequência. Para exibir as propriedades de uma interação, você deve selecioná-la no **Gerenciador de modelos UML**.|
||**Diagrama de Sequência**|O diagrama que exibe uma interação. Para exibir suas propriedades, clique em uma parte vazia do diagrama. **Observação:**  Os nomes do diagrama de sequência, a interação que ele exibe e o arquivo que contém o diagrama podem ser diferentes.|

## <a name="see-also"></a>Consulte também
 [Diagramas de sequência UML: diretrizes](../modeling/uml-sequence-diagrams-guidelines.md) [editar modelos UML e diagramas](../modeling/edit-uml-models-and-diagrams.md) [diagramas de caso de uso UML: referenciar](../modeling/uml-use-case-diagrams-reference.md) [diagramas de classe UML: referenciar](../modeling/uml-class-diagrams-reference.md) diagramas de [componentes UML: referência](../modeling/uml-component-diagrams-reference.md) a [diagramas de componentes UML: referência](../modeling/uml-component-diagrams-reference.md)
