---
title: 'Como: Adicionar validação a classes de entidade | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a68b0314f3c64ce9196b8d48a78844bc81990a92
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665989"
---
# <a name="how-to-add-validation-to-entity-classes"></a>Como adicionar validação a classes de entidade
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Validar* classes de entidade é o processo que confirma que os valores inseridos em objetos de dados estão de acordo com as restrições do esquema de um objeto e também as regras estabelecidas para o aplicativo. Validar dados antes de enviar atualizações para o base de dados subjacente é uma boa prática que reduz erros. Também reduz o número potencial de processamentos entre um aplicativo e o base de dados.

 As [ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) fornecem métodos parciais que permitem aos usuários estender o código gerado pelo designer que é executado durante inserções, atualizações e exclusões de entidades completas e também durante e após alterações de coluna individuais.

> [!NOTE]
> Este tópico fornece as etapas básicas para adicionar validação a classes de entidade usando [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Como pode ser difícil seguir essas etapas genéricas sem referir-se a uma classe de entidade específica, uma explicação que usa dados reais foi fornecida.

## <a name="adding-validation-for-changes-to-the-value-in-a-specific-column"></a>Adicionar validação para alterações ao valor em uma coluna específica
 Este procedimento mostra como validar dados quando o valor em uma coluna é alterado. Porque a validação é executada dentro da definição de classe (em vez de na interface do usuário) será lançada uma exceção se o valor faz com que a validação falhar. Implementar manipulação de erro para o código em seu aplicativo que tenta alterar os valores de coluna.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-validate-data-during-a-columns-value-change"></a>Para validar dados durante o valor de uma coluna alterar

1. Abra ou crie um novo arquivo de classes de LINQ to SQL (arquivo **. dbml** ) no [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Clique duas vezes no arquivo **.dbml** em **Gerenciador de Soluções**.)

2. No o/R Designer, clique com o botão direito do mouse na classe para a qual você deseja adicionar a validação e clique em **Exibir código**.

    O editor de códigos abre com uma classe parcial para a classe de entidade selecionada.

3. Coloque o cursor na classe parcial.

4. Para projetos do Visual Basic:

   1. Expanda a lista **Nome do Método**.

   2. Localize o método **on**_COLUMNNAME_**Changing** para a coluna à qual você deseja adicionar a validação.

   3. Um método `On`*COLUMNNAME* `Changing` é adicionado à classe Partial.

   4. Adicione o seguinte código para primeiro verificar que um valor está inserido e para garantir em que o valor inserido para a coluna é aceitável para seu aplicativo. O argumento de `value` contém o valor proposto, para adicionar a lógica para confirmar que é um valor válido:

      ```vb
      If value.HasValue Then
          ' Add code to ensure that the value is acceptable.
          ' If value < 1 Then
          '    Throw New Exception("Invalid data!")
          ' End If
      End If
      ```

      Para projetos C#:

   5. Porque os projetos C# não gerenciar automaticamente os manipuladores de eventos, você pode usar o IntelliSense para criar métodos parciais de alteração.

       Tipo `partial` e um espaço para acessar a lista de métodos parciais disponíveis. Clique no método de alteração para a coluna que você deseja adicionar validação para. O seguinte código lembra o código que é gerado quando você seleciona um método parcial de alterar:

      ```csharp
      partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)
          {
             throw new System.NotImplementedException();
          }

      ```

## <a name="adding-validation-for-updates-to-an-entity-class"></a>Adicionar validação para atualizações para uma classe de entidade
 Além de verificar valores alterações pendentes, você também pode validar dados quando é feita uma tentativa de atualizar uma classe completa de entidade. A validação durante uma atualização tentada permite que você comparar valores em várias colunas se as regras comerciais exigem esta. O procedimento a seguir mostra como validar quando é feita uma tentativa de atualizar uma classe completa de entidade.

> [!NOTE]
> O código de validação para que as atualizações terminem classes de entidade é executado na classe parcial de <xref:System.Data.Linq.DataContext> (em vez de na classe parcial de uma classe específica de entidade).

#### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>Para validar dados durante uma atualização para uma entidade

1. Abra ou crie um novo arquivo de classes de LINQ to SQL (arquivo **. dbml** ) no [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Clique duas vezes no arquivo **.dbml** em **Gerenciador de Soluções**.)

2. Clique com o botão direito do mouse em uma área vazia do o/R Designer e clique em **Exibir código**.

    O editor de códigos abre com uma classe parcial para `DataContext`.

3. Coloque o cursor na classe parcial para `DataContext`.

4. Para projetos do Visual Basic:

   1. Expanda a lista **Nome do Método**.

   2. Clique em **Atualizar**_ENTITYCLASSNAME_.

   3. Um método*ENTITYCLASSNAME* `Update` é adicionado à classe Partial.

   4. Acessar valores de colunas individuais usando o argumento de `instance` , conforme mostrado no código o seguir:

      ```vb
      If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then
          Dim ErrorMessage As String = "Invalid data!"
          Throw New Exception(ErrorMessage)
      End If
      ```

      Para projetos C#:

   5. Como C# os projetos não geram automaticamente os manipuladores de eventos, você pode usar o IntelliSense para criar o método*CLASSNAME* parcial `Update`.

   6. Tipo `partial` e um espaço para acessar a lista de métodos parciais disponíveis. Clique no método de atualização para a classe que você deseja adicionar validação para. O código a seguir é semelhante ao código gerado quando você seleciona um método parcial `Update`*CLASSNAME* :

      ```csharp
      partial void UpdateCLASSNAME(CLASSNAME instance)
      {
          if ((instance.COLUMNNAME == x) && (instance.COLUMNNAME = y))
          {
              string ErrorMessage = "Invalid data!";
              throw new System.Exception(ErrorMessage);
          }
      }
      ```

## <a name="see-also"></a>Consulte também
 [Ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [validação de dados](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)
