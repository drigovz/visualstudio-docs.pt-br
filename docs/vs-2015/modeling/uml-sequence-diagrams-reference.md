---
title: 'Diagramas de sequência UML: Referência de | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3990d43ae11db3db8eb792883ba62a030cde3a2f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58922280"
---
# <a name="uml-sequence-diagrams-reference"></a>Diagramas de sequência UML: Referência
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No Visual Studio, uma *diagrama de sequência* mostra uma interação, que representa a sequência de mensagens entre instâncias de classes, componentes e subsistemas de atores. Tempo flui para baixo no diagrama, e mostra o fluxo de controle de um participante para outro. Use diagramas de sequência para visualizar instâncias e eventos, em vez de classes e métodos. Mais de uma instância do mesmo tipo pode aparecer no diagrama. Também pode aparecer mais de uma ocorrência da mesma mensagem.  
  
 Diagramas de sequência UML fazem parte de um modelo UML e existem somente dentro de projetos de modelagem UML. Para criar um diagrama de sequência UML, nos **arquitetura** menu, clique em **UML novo ou diagrama de camada**. Saiba mais sobre como criar e desenhar [diagramas de sequência UML](../modeling/uml-sequence-diagrams-guidelines.md) ou [diagramas de modelagem UML](../modeling/edit-uml-models-and-diagrams.md) em geral.  
  
 Para ver quais versões do Visual Studio dão suporte a esse recurso, consulte [suporte de versão para a arquitetura e ferramentas de modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="reading-sequence-diagrams"></a>Diagramas de sequência de leitura  
 A tabela a seguir descreve os elementos que você pode ver em um diagrama de sequência. Saiba mais sobre esses [propriedades dos elementos](../modeling/properties-of-elements-on-uml-sequence-diagrams.md).  
  
 ![Partes de um diagrama de sequência](../modeling/media/uml-sequence.png "UML_Sequence")  
  
|**Forma**|**Elemento**|**Descrição**|  
|---------------|-----------------|---------------------|  
|1|**Linha de vida**|Uma linha vertical que representa a sequência de eventos que ocorrem em um participante durante uma interação, enquanto a linha para baixo, o tempo progride. Esse participante pode ser uma instância de uma classe, componente ou ator.|  
|2|**Ator**|Um participante que é externo ao sistema que você está desenvolvendo.<br /><br /> Você pode fazer com que um símbolo de ator são exibidos na parte superior de uma linha da vida, definindo sua **ator** propriedade.|  
|3|**Mensagem síncrona**|O remetente aguarda uma resposta a uma mensagem síncrona antes de continuar. O diagrama mostra a chamada e retorno. Mensagens síncronas são usadas para representar as chamadas de função comum dentro de um programa, bem como outros tipos de mensagem que se comportam da mesma maneira.|  
|4|**Mensagens assíncronas**|Uma mensagem que não requer uma resposta antes que o remetente continue. Uma mensagem assíncrona mostra apenas uma chamada do remetente. Use para representar a comunicação entre threads separados ou a criação de um novo thread.|  
|5|**Ocorrência de execução**|Vertical sombreado retângulo que aparece na linha de vida de um participante e representa o período de quando o participante é executar uma operação.<br /><br /> A execução começa em que o participante recebe uma mensagem. Se a mensagem inicial era uma mensagem síncrona, a execução termina com uma seta «retornar» de volta ao remetente.|  
|6|**Mensagem de retorno de chamada**|Uma mensagem que retorna para um participante que está aguardando o retorno de uma chamada anterior. A ocorrência de execução resultante aparece na parte superior de um existente.|  
|7|**Mensagem de autoatendimento**|Uma mensagem de um participante a mesmo. A ocorrência de execução resultante aparece na parte superior a execução de envio.|  
|8|**Criar mensagem**|Uma mensagem que cria um participante. Se um participante recebe uma mensagem de criar, ele deve ser o primeiro que ele recebe.|  
|9|**Mensagem encontrada**|Uma mensagem assíncrona do desconhecida ou um participante não especificado.|  
|10|**Mensagem perdida**|Uma mensagem assíncrona desconhecida ou um participante não especificado.|  
|11|**Comentário**|Um comentário pode ser anexado a qualquer ponto em uma linha da vida.|  
|12|**Uso da interação**|Inclui uma sequência de mensagens que são definidos em outro diagrama.<br /><br /> Para criar uma **uso da interação**, clique na ferramenta e, em seguida, percorra as linhas da vida que você deseja incluir.|  
|13|**Fragmento combinado**|Uma coleção de fragmentos. Cada fragmento pode incluir uma ou mais mensagens. Há diferentes tipos de fragmentos combinados. Para obter mais informações, consulte [descrever o fluxo de controle com fragmentos em diagramas de sequência UML](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md).<br /><br /> Para criar um fragmento, uma mensagem com o botão direito, aponte para **envolver com**e, em seguida, clique em um tipo de fragmento.|  
|14|**Protetor de fragmento**|Pode ser usado para o estado de uma condição relevante se o fragmento ocorrerá.<br /><br /> Para definir o protetor, selecione um fragmento, em seguida, selecione o protetor e digite um valor.|  
|**X**|**Evento de destruição**|Representa o ponto no qual o objeto é excluído ou não estarão mais acessíveis. É exibida na parte inferior de cada linha da vida.|  
||**Interação**|A coleção de mensagens e as linhas de vida que é exibida no diagrama de sequência. Para exibir as propriedades de uma interação, selecione-o na **Gerenciador de modelos UML**.|  
||**Diagrama de Sequência**|O diagrama que exibe uma interação. Para exibir suas propriedades, clique em uma parte vazia do diagrama. **Observação:**  Os nomes de diagrama de sequência, a interação que ele exibe, e o arquivo que contém o diagrama pode todos ser diferente.|  
  
## <a name="see-also"></a>Consulte também  
 [Diagramas de sequência de UML: Diretrizes](../modeling/uml-sequence-diagrams-guidelines.md)   
 [Editar modelos e diagramas UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagrama de casos de uso UML: Referência](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagramas de classe UML: Referência](../modeling/uml-class-diagrams-reference.md)   
 [Diagramas de componente UML: Referência](../modeling/uml-component-diagrams-reference.md)   
 [Diagramas de componente UML: referência](../modeling/uml-component-diagrams-reference.md)
