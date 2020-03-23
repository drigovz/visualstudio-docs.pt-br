---
title: 'Etapa 2: Adicionar um objeto aleatório e uma lista de ícones'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 95faea28-eddc-4cfa-95fb-3b34b5a976d7
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f4731778ebb3acbdc3bb7d9b5827c1015541d98
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579426"
---
# <a name="step-2-add-a-random-object-and-a-list-of-icons"></a>Etapa 2: Adicionar um objeto aleatório e uma lista de ícones

Nesta etapa, você cria um conjunto de símbolos correspondentes para o jogo. Cada símbolo é adicionado a duas células aleatórias no TableLayoutPanel do formulário. Para isso, use duas instruções `new` para criar dois objetos. A primeira é um objeto <xref:System.Random>, como o usado no jogo de enigmas de matemática. Ele é usado nesse código para escolher aleatoriamente células no TableLayoutPanel. O segundo objeto, que pode ser novo para você, é um objeto <xref:System.Collections.Generic.List%601>, que é usado para armazenar os símbolos escolhidos aleatoriamente.

## <a name="to-add-a-random-object-and-a-list-of-icons"></a>Para adicionar um objeto aleatório e uma lista de ícones

1. No **Solution Explorer,** escolha *Form1.cs* se estiver usando C#, ou *Form1.vb* se estiver usando o Visual Basic e, em seguida, na barra de menu, escolha **'Código**de **exibição'.** >  Como uma alternativa, é possível pressionar a tecla **F7** ou clicar duas vezes em **Form1** no **Gerenciador de Soluções**.

     Isso exibe o módulo de código por trás de Form1.

2. No código existente, adicione o código a seguir.

     [!code-csharp[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/CSharp/step-2-add-a-random-object-and-a-list-of-icons_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#1](../ide/codesnippet/VisualBasic/step-2-add-a-random-object-and-a-list-of-icons_1.vb)]

      > [!IMPORTANT]
      > Use o controle de linguagem de programação no canto superior direito desta página para exibir o trecho de código C# ou o trecho de código Visual Basic.<br><br>![Controle de linguagem de programação para Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

      Se você estiver usando C#, certifique-se de colocar o código após a`public partial class Form1 : Form`abertura da cinta encaracolada e logo após a declaração da classe (). Se estiver usando o Visual Basic, coloque o código logo depois da declaração de classe (`Public Class Form1`).

3. Ao adicionar o objeto de lista, observe a janela do **IntelliSense** que é aberta. A seguir está um exemplo C#, mas texto semelhante aparece quando você adiciona uma lista no Visual Basic.

     ![Janela Propriedades mostrando o evento de clique](../ide/media/express_listintellisense.png)<br/>***Janela IntelliSense***

    > [!NOTE]
    > A janela do IntelliSense aparece apenas quando você insere código manualmente. Se você copiar e colar o código, ela não aparecerá.

     Se você observar o código (e fizer observações) em pequenas seções, será mais fácil entender. Seus programas podem usar objetos de lista para acompanhar muitos tipos de item diferentes. Uma lista pode manter números, valores verdadeiro/falso, texto ou outros objetos. Você pode ter até mesmo um objeto de lista que mantém outros objetos de lista. Os itens em uma lista são chamados de elementos e cada lista mantém apenas um tipo de elemento. Desse modo, uma lista de números pode manter apenas números; não é possível adicionar texto a essa lista. Da mesma forma, não é possível adicionar número a uma lista de valores verdadeiro/falso.

     Quando você cria um objeto `List` usando uma declaração `new`, é preciso especificar o tipo de dados que deseja armazenar nele. É por esse motivo que a dica de ferramenta na parte superior da janela do **IntelliSense** mostra os tipos de elementos na lista. Além disso, isso `List<string>` é o que `List(Of String)` (em C#) e (no Visual Basic) significa: é um `List` objeto que contém elementos do tipo de `string` dados. Uma cadeia de caracteres é o que seu programa usa para armazenar texto, que é o que a dica de ferramenta à direita da janela do **IntelliSense** está informando a você.

4. Considere por que no Visual Basic uma matriz temporária deve ser criada primeiro, mas em C#, a lista pode ser criada com uma declaração. Isso porque a língua C# tem *iniciadores de coleção,* que preparam a lista para aceitar valores. No Visual Basic, você pode usar um inicializador de coleção. No entanto, para compatibilidade com a versão anterior do Visual Basic, é recomendável usar o código anterior.

     Quando você usa um inicializador de coleção com uma instrução `new`, depois que o novo objeto de lista é criado, o programa o preenche com os dados fornecidos entre chaves. Nesse caso, você obtém uma lista de cadeias de caracteres denominadas ícones e essa lista será inicializada para que contenha dezesseis cadeias de caracteres. Cada uma dessas cadeias de caracteres é uma única letra e elas correspondem aos ícones que estarão nos rótulos. Desse modo, o jogo terá um par de pontos de exclamação, um par de letras N maiúsculas, um par de vírgulas, e assim por diante. (Quando esses caracteres são definidos para a fonte Webdings, eles aparecerão como símbolos, como um ônibus, uma bicicleta, uma aranha e assim por diante.) Seu objeto de lista terá dezesseis strings ao todo, uma para cada célula no painel TableLayoutPanel.

    > [!NOTE]
    > No Visual Basic, você obtém o mesmo resultado, mas primeiro as cadeias de caracteres são colocadas em uma matriz temporária, que é então convertida em um objeto de lista. Uma matriz é semelhante a uma lista, exceto, por exemplo, as matrizes que são criadas com um tamanho fixo. As listas podem ser reduzidas e aumentadas, conforme a necessidade, que é importante nesse programa.

## <a name="to-continue-or-review"></a>Para continuar ou revisar

- Para ir para a próxima etapa do tutorial, consulte [**Passo 3: Atribuir um ícone aleatório a cada rótulo**](../ide/step-3-assign-a-random-icon-to-each-label.md).

- Para retornar à etapa tutorial anterior, consulte [Passo 1: Crie um projeto e adicione uma tabela ao seu formulário](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md).
