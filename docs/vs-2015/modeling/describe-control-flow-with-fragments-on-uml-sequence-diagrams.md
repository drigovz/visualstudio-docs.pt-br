---
title: Descrever o fluxo de controle com fragmentos em diagramas de sequência UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.interactionoperand
- vs.teamarch.sequencediagram.combinedfragment
helpviewer_keywords:
- UML sequence diagrams, control flow
- UML sequence diagrams, fragments
- sequence diagrams, fragments
- sequence diagrams, control flow
ms.assetid: efcc0949-be7e-4cf4-99ef-47c36b3803ae
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40f48891107c2eb3250b6b050e00c3650812d386
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669812"
---
# <a name="describe-control-flow-with-fragments-on-uml-sequence-diagrams"></a>Descrever o fluxo de controle com fragmentos em diagramas de sequência UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Em um diagrama de sequência UML, os *fragmentos combinados* permitem mostrar loops, ramificações e outras alternativas.

 Um fragmento combinado consiste em um ou mais *operandos de interação*, e cada um deles inclui uma ou mais mensagens, usos de interação ou fragmentos combinados.

> [!NOTE]
> Este tópico é sobre fragmentos em diagramas de sequência. Para obter mais informações sobre como ler diagramas de sequência UML, consulte [diagramas de sequência UML: referência](../modeling/uml-sequence-diagrams-reference.md). Para obter mais informações sobre como desenhar diagramas de sequência UML, consulte [diagramas de sequência UML: diretrizes](../modeling/uml-sequence-diagrams-guidelines.md).

 ![Fragmento combinado com dois operandos de interação](../modeling/media/uml-seqfragments.png "UML_SeqFragments")

 Os elementos mostrados na figura são os seguintes.

1. Um fragmento combinado. Há vários tipos de fragmentos combinados. Este exemplo é um fragmento combinado Alt, que pode ser usado para mostrar que sequências alternativas de mensagens podem ocorrer.

2. Operandos de interação. Cada fragmento combinado contém pelo menos um operando de interação, que pode conter mensagens, usos de interação e fragmentos combinados menores. Neste exemplo, o fragmento combinado Alt tem duas operações de interação, mostrando duas sequências alternativas de mensagens.

3. Você pode selecionar cada operando de interação separadamente clicando nele dentro dele. Neste exemplo, o operando de interação superior está selecionado, para que seu limite possa ser visto. Normalmente, somente a linha de divisão entre os operandos de interação é visível.

    > [!NOTE]
    > Para selecionar o operando de interação superior, você não deve clicar muito perto da parte superior do fragmento combinado.

4. Protege. Você pode dar a cada operando de interação uma proteção. Isso descreve a condição sob a qual as mensagens dentro do operando de interação serão executadas.

## <a name="creating-combined-fragments"></a>Criando fragmentos combinados
 Para obter uma lista dos tipos de fragmento que você pode criar, consulte [tipos de fragmento combinado](#KindsOfFragment).

#### <a name="to-create-a-combined-fragment"></a>Para criar um fragmento combinado

1. Selecione uma mensagem ou uma sequência de mensagens, todas iniciadas na mesma linha de vida ou ocorrência de execução.

   > [!NOTE]
   > Se você selecionar mais de uma mensagem, elas deverão formar uma sequência ininterrupta.

2. Clique com o botão direito do mouse em uma das mensagens, aponte para **surround com**e clique no tipo de fragmento combinado desejado, como o **fragmento combinado Alt**.

    Um novo fragmento combinado é exibido. O cabeçalho indica o tipo de fragmento combinado que você selecionou, como **ALT**.

    Dentro do fragmento combinado, há um fragmento que contém as mensagens que você selecionou.

   Você pode adicionar mais operandos de interação a alguns tipos de fragmento combinado.

   Depois de reorganizar as mensagens em um fragmento combinado, escolha **reorganizar layout** no menu de atalho para redimensionar o quadro de fragmento combinado.

#### <a name="to-add-a-new-interaction-operand-to-a-combined-fragment"></a>Para adicionar um novo operando de interação a um fragmento combinado

1. Clique com o botão direito do mouse em um espaço em branco dentro do operando de interação (2), fora de qualquer fragmento contido e abaixo do título do fragmento combinado.

2. Aponte para **Adicionar**.

3. Clique em **operando de interação antes**ou **operando de interação depois**.

4. Você pode adicionar mensagens dentro do novo operando de interação usando as ferramentas de mensagem ou copiando e colando as mensagens existentes.

   Você pode definir a propriedade **Guard** de um operando de interação para descrever as condições em que as mensagens dentro dela são executadas. Por exemplo, em um fragmento combinado de **loop** , você pode usar o Guard para especificar a condição durante a qual o loop continua. Em um fragmento combinado **ALT** , você pode especificar uma condição separada para cada operando de interação.

#### <a name="to-set-the-guard-of-an-interaction-operand"></a>Para definir o protetor de um operando de interação

1. Clique em um espaço em branco dentro do operando de interação (2), fora de qualquer fragmento contido.

    Uma borda de seleção aparece em torno do operando de interação e em torno da condição de proteção.

    O título na janela **Propriedades** mostra o **operando de interação**.

2. Digite a condição de proteção.

    A condição aparecerá próximo à parte superior do fragmento (4).

   Você pode definir as propriedades de alguns tipos de fragmentos combinados.

#### <a name="to-set-or-view-the-properties-of-a-combined-fragment"></a>Para definir ou exibir as propriedades de um fragmento combinado

- Clique com o botão direito do mouse no título do fragmento combinado e clique em **Propriedades**.

    > [!NOTE]
    > Diferentes tipos de fragmento combinado têm propriedades diferentes.

## <a name="kinds-of-combined-fragment"></a><a name="KindsOfFragment"></a> Tipos de fragmento combinado

### <a name="fragments-describing-control-flow"></a>Fragmentos que descrevem o fluxo de controle
 Um diagrama de sequência simples mostra apenas uma sequência típica. Você pode usar os seguintes tipos de fragmentos combinados para descrever as variações que podem ocorrer em ocasiões diferentes.

|Tipo de fragmento|Descrição|
|-------------------|-----------------|
|**Opt**|Opcional. Inclui uma seqüência que pode ou não acontecer. Você pode especificar, na proteção, a condição sob a qual ela ocorre.|
|**Alt**|Contém uma lista de fragmentos que contêm sequências alternativas de mensagens. Apenas uma sequência ocorre em qualquer ocasião.<br /><br /> Você pode colocar um protetor em cada fragmento para indicar sob qual condição ele pode ser executado. Um protetor de **else** indica um fragmento que deve ser executado se nenhuma outra proteção for verdadeira. Se todas as proteções forem falsas e não houver **mais**, nenhum dos fragmentos será executado.|
|**While**|O fragmento repete um número de vezes. Você pode indicar na proteção a condição sob a qual ela deve se repetir.<br /><br /> Os fragmentos combinados de loop têm as propriedades **min** e **Max**, que indicam o número mínimo e máximo de vezes que o fragmento pode ser repetido. O padrão não é restrição.|
|**Interrupção**|Se esse fragmento for executado, o restante da sequência será abandonado. Você pode usar a proteção para indicar a condição em que ocorrerá a interrupção.|
|**Nominal**|Paralelo. Os eventos nos fragmentos podem ser intercalados.|
|**Crítico**|Usado em um fragmento par ou Seq. Indica que as mensagens neste fragmento não devem ser intercaladas com outras mensagens.|
|**Seq**|Há dois ou mais fragmentos de operando. As mensagens que envolvem a mesma linha de vida devem ocorrer na ordem dos fragmentos. Quando eles não envolvem as mesmas linhas de vida, as mensagens de fragmentos diferentes podem ser intercaladas em paralelo.|
|**Strict**|Há dois ou mais fragmentos de operando. Os fragmentos devem ocorrer na ordem fornecida.|

### <a name="fragments-about-how-to-interpret-the-sequence"></a>Fragmentos sobre como interpretar a sequência
 Por padrão, o diagrama de sequência indica uma série de mensagens que podem ocorrer. No sistema em execução, outras mensagens podem acontecer de você não ter optado por mostrar no diagrama.

 Os tipos de fragmento a seguir podem ser usados para alterar essa interpretação.

|Tipo de fragmento|Descrição|
|-------------------|-----------------|
|**Aconselhável**|Especifica uma lista das mensagens que este fragmento descreve. Outras mensagens podem ocorrer no sistema em execução, mas não são significativas para os fins desta descrição.<br /><br /> Digite a lista na propriedade **messages** .|
|**Ignorar**|Uma lista das mensagens que este fragmento não descreve. Eles podem ocorrer no sistema em execução, mas não são significativos para os fins desta descrição.<br /><br /> Digite a lista na propriedade **messages** .|
|**Assert**|O fragmento do operando especifica as únicas sequências válidas. Normalmente usado em um fragmento de considere ou ignorar.|
|**Neg**|A sequência mostrada neste fragmento não deve acontecer. Normalmente usado em um fragmento de considere ou ignorar.|

## <a name="see-also"></a>Consulte Também
 [Diagramas de sequência UML: diretrizes](../modeling/uml-sequence-diagrams-guidelines.md) [diagramas de sequência UML: referência](../modeling/uml-sequence-diagrams-reference.md) [Editar diagramas e modelos UML](../modeling/edit-uml-models-and-diagrams.md)
