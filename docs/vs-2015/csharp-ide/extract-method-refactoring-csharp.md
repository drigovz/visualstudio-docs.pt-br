---
title: Extrair refatoração de método (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Method
- Extract Method refactoring operation [C#]
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e6d5e7913a7433fd4b30da490f33dd614c3e2b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667541"
---
# <a name="extract-method-refactoring-c"></a>Refatoração Extrair Método (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O **método Extract** é uma operação de refatoração que fornece uma maneira fácil de criar um novo método a partir de um fragmento de código em um membro existente.

 Usando o **método Extract**, você pode criar um novo método extraindo uma seleção de código de dentro do bloco de código de um membro existente. O novo método extraído contém o código selecionado, e o código selecionado no membro existente é substituído por uma chamada para o novo método. Transformar um fragmento de código em seu próprio método permite reorganizar com rapidez e precisão o código para melhorar a reutilização e a legibilidade.

 O **método Extract** tem os seguintes benefícios:

- Incentiva as melhores práticas de codificação enfatizando métodos discretos e reutilizáveis.

- Incentiva o código de autodocumentação por meio de uma boa organização.

     Quando nomes descritivos são usados, métodos de alto nível podem ler mais como uma série de comentários.

- Incentiva a criação de métodos mais refinados para simplificar a substituição.

- Reduz a duplicação de código.

### <a name="to-use-extract-method"></a>Para usar o método Extract

1. Crie um aplicativo de console chamado `ExtractMethod` e, em seguida, substitua `Program` pelo código de exemplo a seguir.

    ```csharp
    class A
    {
        const double PI = 3.141592;

        double CalculatePaintNeeded(double paintPerUnit, double radius)
        {
            // Select any of the following:
            // 1. The entire next line of code.
            // 2. The right-hand side of the next line of code.
            // 3. Just "PI *" of the right-hand side of the next line
            //    of code (to see the prompt for selection expansion).
            // 4.  All code within the method body.
            // ...Then invoke Extract Method.

            double area = PI * radius * radius;

            return area / paintPerUnit;
        }
    }
    ```

2. Selecione o fragmento de código que você deseja extrair:

    ```csharp
    double area = PI * radius * radius;
    ```

3. No menu **refatorar** , clique em **extrair método**.

     A caixa de diálogo **extrair método** é exibida.

     Como alternativa, você também pode digitar o atalho de teclado CTRL + R, M para exibir a caixa de diálogo **extrair método** .

     Você também pode clicar com o botão direito do mouse no código selecionado, apontar para **refatorar**e clicar em **extrair método** para exibir a caixa de diálogo **extrair método** .

4. Especifique um nome para o novo método, como `CircleArea` , na caixa **nome do novo método** .

     Uma visualização da nova assinatura de método é exibida na **assinatura do método de visualização**.

5. Clique em **OK**.

## <a name="remarks"></a>Comentários
 Quando você usa o comando **Extract Method** , o novo método é inserido seguindo o membro de origem na mesma classe.

## <a name="partial-types"></a>Tipos parciais
 Se a classe for um tipo parcial, o **método Extract** gerará o novo método imediatamente após o membro de origem. O **método Extract** determina a assinatura do novo método, criando um método estático quando nenhum dado de instância é referenciado pelo código no novo método.

## <a name="generic-type-parameters"></a>Parâmetros de tipo genérico
 Quando você extrai um método que tem um parâmetro de tipo genérico irrestrito, o código gerado não adiciona o `ref` modificador a esse parâmetro, a menos que um valor seja atribuído a ele. Se o método extraído der suporte a tipos de referência como argumento de tipo genérico, você deverá adicionar manualmente o `ref` modificador ao parâmetro na assinatura do método.

## <a name="anonymous-methods"></a>Métodos anônimos
 Se você tentar extrair parte de um método anônimo que inclui uma referência a uma variável local que é declarada ou referenciada fora do método anônimo, o Visual Studio avisará sobre possíveis alterações de semântica.

 Quando um método anônimo usa o valor de uma variável local, o valor é obtido no momento em que o método anônimo é executado. Quando um método anônimo é extraído em outro método, o valor da variável local é obtido no momento da chamada para o método extraído.

 O exemplo a seguir ilustra essa alteração semântica. Se esse código for executado, **11** será impresso no console. Se você usar o **método Extract** para extrair a região do código que está marcada pelos comentários de código em seu próprio método e, em seguida, executar o código refatorado, **10** será impresso no console.

```csharp
class Program
{
    delegate void D();
    D d;
    static void Main(string[] args)
    {
        Program p = new Program();
        int i = 10;
        /*begin extraction*/
            p.d = delegate { Console.WriteLine(i++); };
        /*end extraction*/
        i++;
        p.d();
    }
}
```

 Para contornar essa situação, faça as variáveis locais que são usadas nos campos de método anônimo da classe.

## <a name="see-also"></a>Consulte Também
 [Refatoração (C#)](../csharp-ide/refactoring-csharp.md)