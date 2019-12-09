---
title: Renomear refatoração (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Rename
- Rename refactoring [C#]
ms.assetid: 268942fc-b142-4dfa-8d90-bedd548c2e4f
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0db7696268e5e3d24d005fbf35a08b330f2dc849
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667474"
---
# <a name="rename-refactoring-c"></a>Refatoração Renomear (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Rename** é um recurso de refatoração no IDE (ambiente de desenvolvimento integrado) do Visual Studio que fornece uma maneira fácil de renomear identificadores para símbolos de código como campos, variáveis locais, métodos, namespaces, propriedades e tipos. **Rename** pode ser usado para alterar os nomes em comentários e em cadeias de caracteres e para alterar as declarações e chamadas de um identificador.

> [!NOTE]
> Ao usar o controle do código-fonte para o Visual Studio, obtenha a versão mais recente das fontes antes de tentar executar a refatoração de renomeação.

 A refatoração de renomeação está disponível nos seguintes recursos do Visual Studio:

|Recurso|Comportamento da refatoração no IDE|
|-------------|----------------------------------------|
|Editor de Códigos|No editor de código, a refatoração de renomeação está disponível quando você posiciona o cursor em determinados tipos de símbolos de código. Quando o cursor estiver nessa posição, você poderá invocar o comando **renomear** digitando o atalho de teclado (Ctrl + r, CTRL + r) ou selecionando o comando **renomear** em uma marca inteligente, menu de atalho ou no menu **Refactor** .|
|Exibição de Classe|Quando você seleciona um identificador em Modo de Exibição de Classe, a refatoração de renomeação está disponível no menu de atalho e no menu de **refatoração** .|
|Pesquisador de Objetos|Quando você seleciona um identificador no Pesquisador de objetos, a refatoração Renomear só está disponível no menu **refatorar** .|
|Grade de propriedades do Designer de Formulários do Windows|Na **grade de propriedades** do designer de formulários do Windows, a alteração do nome de um controle iniciará uma operação de renomeação para esse controle. A caixa de diálogo **renomear** não será exibida.|
|Gerenciador de Soluções|No **Gerenciador de soluções**, um comando de **renomeação** está disponível no menu de atalho. Se o arquivo de origem selecionado contiver uma classe cujo nome de classe é igual ao nome do arquivo, você poderá usar esse comando para renomear simultaneamente o arquivo de origem e executar refatoração de renomeação.<br /><br /> Por exemplo, se você criar um aplicativo padrão baseado no Windows e, em seguida, renomear Form1.cs como TestForm.cs, o nome do arquivo de origem Form1.cs será alterado para TestForm.cs e a classe Form1 e todas as referências a essa classe serão renomeadas como TestForm. **Observação:**  O comando **desfazer** (Ctrl + Z) somente desnomeará a refatoração no código e não alterará o nome do arquivo de volta para o nome original. <br /><br /> Se o arquivo de origem selecionado não contiver uma classe cujo nome é o mesmo que o nome do arquivo, o comando **renomear** em **Gerenciador de soluções** renomeará apenas o arquivo de origem e não executará a refatoração de renomeação.|

## <a name="rename-operations"></a>Renomear operações
 Quando você executa **Rename**, o mecanismo de refatoração executa uma operação de renomeação específica para cada símbolo de código, conforme descrito na tabela a seguir.

|Símbolo de código|Renomear operação|
|-----------------|----------------------|
|Campo|Altera a declaração e os usos do campo para o novo nome.|
|Variável local|Altera a declaração e os usos da variável para o novo nome.|
|Método|Altera o nome do método e todas as referências a esse método para o novo nome. **Observação:**  Quando você renomeia um método de extensão, a operação de renomeação é propagada para todas as instâncias do método que estão no escopo, independentemente de o método de extensão estar sendo usado como um método estático ou um método de instância. Para obter mais informações, consulte [Métodos de extensão](https://msdn.microsoft.com/library/175ce3ff-9bbf-4e64-8421-faeb81a0bb51).|
|espaço de nome|Altera o nome do namespace para o novo nome na declaração, todas as instruções `using` e nomes totalmente qualificados. **Observação:**  Ao renomear um namespace, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] também atualiza a propriedade de **namespace padrão** na página do **aplicativo** do **Designer de projeto**. Essa propriedade não pode ser redefinida selecionando **desfazer** no menu **Editar** . Para redefinir o valor da propriedade de **namespace padrão** , você deve modificar a propriedade no **Designer de projeto**. Para obter mais informações, consulte [página do aplicativo](../ide/reference/application-page-project-designer-csharp.md).|
|propriedade|Altera a declaração e os usos da propriedade para o novo nome.|
|Digite|Altera todas as declarações e todos os usos do tipo para o novo nome, incluindo construtores e destruidores. Para tipos parciais, a operação de renomeação será propagada para todas as partes.|

#### <a name="to-rename-an-identifier"></a>Para renomear um identificador

1. Crie um aplicativo de console chamado `RenameIdentifier` e, em seguida, substitua `Program` pelo código de exemplo a seguir.

    ```csharp
    class ProtoClassA
    {
        // Invoke on 'MethodB'.
        public void MethodB(int i, bool b) { }
    }

    class ProtoClassC
    {
        void D()
        {
            ProtoClassA MyClassA = new ProtoClassA();

            // Invoke on 'MethodB'.
            MyClassA.MethodB(0, false);
        }
    }
    ```

2. Coloque o cursor em `MethodB`, na declaração do método ou na chamada do método.

3. No menu **refatorar** , selecione **renomear**. A caixa de diálogo **renomear** é exibida.

     Você também pode clicar com o botão direito do mouse no cursor, apontar para **refatorar** no menu de contexto e clicar em **renomear** para exibir a caixa de diálogo **renomear** .

4. No campo **novo nome** , digite `MethodC`.

5. Marque a caixa de seleção **Pesquisar em comentários** .

6. Clique em **OK**.

7. Na caixa de diálogo **Visualizar alterações** , clique em **aplicar**.

#### <a name="to-rename-an-identifier-using-smart-tags"></a>Para renomear um identificador usando marcas inteligentes

1. Crie um aplicativo de console chamado `RenameIdentifier` e, em seguida, substitua `Program` pelo código de exemplo a seguir.

    ```csharp
    class ProtoClassA
    {
        // Invoke on 'MethodB'.
        public void MethodB(int i, bool b) { }
    }

    class ProtoClassC
    {
        void D()
        {
            ProtoClassA MyClassA = new ProtoClassA();

            // Invoke on 'MethodB'.
            MyClassA.MethodB(0, false);
        }
    }
    ```

2. Na declaração de `MethodB`, digite ou Backspace sobre o identificador do método. Um prompt de marca inteligente aparecerá abaixo desse identificador.

    > [!NOTE]
    > Você só pode invocar refatoração de renomeação usando marcas inteligentes na declaração de um identificador.

3. Digite o atalho de teclado SHIFT + ALT + F10 e, em seguida, pressione a seta para baixo para exibir o menu de marca inteligente.

     \- ou -

     Mova o ponteiro do mouse sobre o prompt de marca inteligente para exibir a marca inteligente. Em seguida, mova o ponteiro do mouse sobre a marca inteligente e clique na seta para baixo para exibir o menu de marca inteligente.

4. Selecione o item de menu **Renomear ' \<identifer1 > ' para ' \<identifier2 > '** para invocar a refatoração de renomeação sem uma visualização das alterações em seu código. Todas as referências a **\<identifer1 >** serão atualizadas automaticamente para **\<identifier2 >** .

     \- ou -

     Selecione o item de menu **renomear com visualização** para invocar a refatoração de renomeação com uma visualização das alterações em seu código. A caixa de diálogo **Visualizar alterações** será exibida.

## <a name="remarks"></a>Comentários

## <a name="renaming-implemented-or-overridden-members"></a>Renomeando Membros implementados ou substituídos
 Quando você **renomeia** um membro que implementa/substitui ou é implementado/substituído por membros em outros tipos, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] exibe uma caixa de diálogo que diz que a operação de renomeação causará atualizações em cascata. Se você clicar em **continuar**, o mecanismo de refatoração localizará e renomeará recursivamente todos os membros em tipos base e derivados que têm implementa/substitui as relações com o membro que está sendo renomeado.

 O exemplo de código a seguir contém membros com relações de implementações/substituições.

 [!code-csharp[CsUsingCsIDERefactor#1](../snippets/csharp/VS_Snippets_VBCSharp/CsUsingCsIDERefactor/CS/Class1.cs#1)]

 No exemplo anterior, renomear `C.Method()` também renomeará `Ibase.Method()` porque `C.Method()` implementa `Ibase.Method()`. Em seguida, o mecanismo de refatoração vê recursivamente que `Ibase.Method()` é implementada por `Derived.Method()` e renomeia `Derived.Method()`. O mecanismo de refatoração não renomeia `Base.Method()`, porque `Derived.Method()` não substitui `Base.Method()`. O mecanismo de refatoração é interrompido aqui, a menos que você tenha a opção renomear **sobrecargas** marcada na caixa de diálogo **renomear** .

 Se a opção **Renomear sobrecargas** estiver marcada, o mecanismo de refatoração renomeará `Derived.Method(int i)` porque ele sobrecarrega `Derived.Method()`, `Base.Method(int i)` porque ele é substituído por `Derived.Method(int i)` e `Base.Method()` porque é uma sobrecarga de `Base.Method(int i)`.

> [!NOTE]
> Quando você renomeia um membro que foi definido em um assembly referenciado, uma caixa de diálogo explica que a renomeação causará erros de compilação.

## <a name="renaming-properties-of-anonymous-types"></a>Renomeando Propriedades de tipos anônimos
 Quando você renomear uma propriedade em tipos anônimos, a operação de renomeação será propagada para propriedades em outros tipos anônimos que têm as mesmas propriedades. Os exemplos a seguir ilustram esse comportamento.

```csharp
var a = new { ID = 1};
var b = new { ID = 2};
```

 No código anterior, renomear `ID` mudará `ID` em ambas as instruções porque elas têm o mesmo tipo anônimo subjacente.

```csharp
var companyIDs =
    from c in companylist
    select new { ID = c.ID, Name = c.Name};

var orderIDs =
    from o in orderlist
    select new { ID = o.ID, Item = o.Name};
```

 No código anterior, renomear `ID` renomeará apenas uma instância de `ID` porque `companyIDs` e `orderIDs` não têm as mesmas propriedades.

## <a name="see-also"></a>Consulte também
 [Tipos anônimos](https://msdn.microsoft.com/library/59c9d7a4-3b0e-475e-b620-0ab86c088e9b) [deC#refatoração ()](../csharp-ide/refactoring-csharp.md)