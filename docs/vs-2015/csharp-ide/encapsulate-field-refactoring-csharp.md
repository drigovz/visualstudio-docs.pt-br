---
title: Encapsular refatoração de campoC#() | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b4f5ddbe7eab925b06584f00b04bed3c74e9811
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667565"
---
# <a name="encapsulate-field-refactoring-c"></a>Refatoração Encapsular Campo (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A operação de refatoração de **campo encapsular** permite que você crie rapidamente uma propriedade de um campo existente e, em seguida, atualize diretamente seu código com referências à nova propriedade.

 Quando um [campo](https://msdn.microsoft.com/library/3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7) é [público](https://msdn.microsoft.com/library/0ae45d16-a551-4b74-9845-57208de1328e), outros objetos têm acesso direto a esse campo e podem modificá-lo, sem ser detectado pelo objeto que possui esse campo. Ao usar [Propriedades](https://msdn.microsoft.com/library/e295a8a2-b357-4ee7-a12e-385a44146fa8) para encapsular esse campo, você pode não permitir o acesso direto a campos.

 Para criar a nova propriedade, a operação de **campo Encapsulate** altera o modificador de acesso do campo que você deseja encapsular para [privado](https://msdn.microsoft.com/library/654c0bb8-e6ac-4086-bf96-7474fa6aa1c8)e, em seguida, gera acessadores [Get](https://msdn.microsoft.com/library/a52de048-fbe0-41b0-82ec-8e4ac04d3a71) e [set](https://msdn.microsoft.com/library/30d7e4e5-cc2e-4635-a597-14a724879619) para esse campo. Em alguns casos, apenas um acessador `get` é gerado, como quando o campo é declarado como somente leitura.

 O mecanismo de refatoração atualiza seu código com referências à nova propriedade nas áreas especificadas na seção **Atualizar referências** da caixa de diálogo **encapsular campo** .

### <a name="to-create-a-property-from-a-field"></a>Para criar uma propriedade a partir de um campo

1. Crie um aplicativo de console chamado `EncapsulateFieldExample` e, em seguida, substitua `Program` pelo código de exemplo a seguir.

    ```csharp
    class Square
    {
        // Select the word 'width' and then use Encapsulate Field.
        public int width, height;
    }
    class MainClass
    {
        public static void Main()
        {
            Square mySquare = new Square();
            mySquare.width = 110;
            mySquare.height = 150;
            // Output values for width and height.
            Console.WriteLine("width = {0}", mySquare.width);
            Console.WriteLine("height = {0}", mySquare.height);
        }
    }
    ```

2. No [Editor de código](../ide/writing-code-in-the-code-and-text-editor.md), coloque o cursor na declaração, no nome do campo que você deseja encapsular. No exemplo a seguir, coloque o cursor na palavra `width`:

    ```csharp
    public int width, height;
    ```

3. No menu **refatorar** , clique em **encapsular campo**.

     A caixa de diálogo **encapsular campo** é exibida.

     Você também pode digitar o atalho de teclado CTRL + R, E para exibir a caixa de diálogo **encapsular campo** .

     Você também pode clicar com o botão direito do mouse no cursor, apontar para **refatorar**e, em seguida, clicar em **encapsular campo** para exibir a caixa de diálogo **encapsular campo** .

4. Especifique as configurações.

5. Pressione ENTER ou clique no botão **OK** .

6. Se você tiver selecionado a opção **Visualizar alterações de referência** , a janela **Visualizar alterações de referência** será aberta. Clique no botão **aplicar** .

     O seguinte `get` e `set` código do acessador é exibido no arquivo de origem:

    ```csharp
    public int Width
    {
        get { return width; }
        set { width = value; }
    }
    ```

     O código no método `Main` também é atualizado para o novo nome da propriedade `Width`.

    ```csharp
    Square mySquare = new Square();
    mySquare.Width = 110;
    mySquare.height = 150;
    // Output values for width and height.
    Console.WriteLine("width = {0}", mySquare.Width);
    ```

## <a name="remarks"></a>Comentários
 A operação de **campo Encapsulate** só é possível quando o cursor está posicionado na mesma linha que a declaração de campo.

 Para declarações que declaram vários campos, o **campo Encapsulate** usa a vírgula como um limite entre os campos e inicia a refatoração no campo que é mais próximo do cursor e na mesma linha que o cursor. Você também pode especificar qual campo deseja encapsular selecionando o nome desse campo na declaração.

 O código gerado por essa operação de refatoração é modelado pelo recurso encapsular trechos de código de campo. Os snippets de código são modificáveis. Para obter mais informações, consulte [Snippets de Código](../ide/code-snippets.md).

## <a name="see-also"></a>Consulte também
 [Trechos de códigoC#Visual](../csharp-ide/refactoring-csharp.md) [ C# ](../ide/visual-csharp-code-snippets.md) de refatoração ()