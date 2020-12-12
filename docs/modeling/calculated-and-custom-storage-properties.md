---
title: Propriedades calculadas e de armazenamento personalizado
description: Saiba como todas as propriedades de domínio em uma DSL (linguagem específica de domínio) podem ser exibidas para o usuário no diagrama e no seu Gerenciador de idiomas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c50d205745917b3af7de638a17921f4bcdca509
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363543"
---
# <a name="calculated-and-custom-storage-properties"></a>Propriedades calculadas e de armazenamento personalizado
Todas as propriedades de domínio em uma DSL (linguagem específica de domínio) podem ser exibidas para o usuário no diagrama e no seu Gerenciador de idiomas e podem ser acessadas pelo código do programa. No entanto, as propriedades são diferentes na forma como os valores são armazenados.

## <a name="kinds-of-domain-properties"></a>Tipos de propriedades de domínio
 Na definição de DSL, você pode definir o **tipo** de uma propriedade de domínio, conforme listado na tabela a seguir:

|Tipo de propriedade de domínio|Descrição|
|-|-|
|**Padrão** (padrão)|Uma propriedade de domínio que é salva na *loja* e serializada para o arquivo.|
|**Calculadas**|Uma propriedade de domínio somente leitura que não é salva no repositório, mas é calculada a partir de outros valores.<br /><br /> Por exemplo, `Person.Age` pode ser calculado a partir de `Person.BirthDate` .<br /><br /> Você precisa fornecer o código que executa o cálculo. Normalmente, você calcula o valor de outras propriedades de domínio. No entanto, você também pode usar recursos externos.|
|**Armazenamento personalizado**|Uma propriedade de domínio que não é salva diretamente no repositório, mas pode ser Get e Set.<br /><br /> Você precisa fornecer os métodos que obtêm e definem o valor.<br /><br /> Por exemplo, `Person.FullAddress` pode ser armazenado em `Person.StreetAddress` , `Person.City` e `Person.PostalCode` .<br /><br /> Você também pode acessar recursos externos, por exemplo, para obter e definir valores de um banco de dados.<br /><br /> Seu código não deve definir valores no repositório quando `Store.InUndoRedoOrRollback` for verdadeiro. Confira [Transações e setters personalizados](#setters).|

## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>Fornecendo o código para uma propriedade de armazenamento calculada ou personalizada
 Se você definir o tipo de uma propriedade de domínio para armazenamento calculado ou personalizado, precisará fornecer métodos de acesso. Quando você cria sua solução, um relatório de erros informa o que é necessário.

#### <a name="to-define-a-calculated-or-custom-storage-property"></a>Para definir uma propriedade de armazenamento calculada ou personalizada

1. Em DslDefinition. DSL, selecione a propriedade domínio no diagrama ou no Gerenciador de **DSL**.

2. Na janela **Propriedades** , defina o campo **tipo** como armazenamento **calculado** ou **personalizado**.

     Verifique se você também definiu seu **tipo** para o que deseja.

3. Clique em **transformar todos os modelos** na barra de ferramentas de **Gerenciador de soluções**.

4. No menu **Compilar**, clique em **Compilar Solução**.

     Você recebe a seguinte mensagem de erro: "*yourClass* não contém uma definição para obter *suaproperty*."

5. Clique duas vezes na mensagem de erro.

     Dsl\GeneratedCode\DomainClasses.cs ou DomainRelationships.cs é aberto. Acima da chamada do método realçado, um comentário solicita que você forneça uma implementação para obter *suaproperty*().

    > [!NOTE]
    > Esse arquivo é gerado de DslDefinition. DSL. Se você editar esse arquivo, suas alterações serão perdidas na próxima vez que você clicar em **transformar todos os modelos**. Em vez disso, adicione o método necessário em um arquivo separado.

6. Crie ou abra um arquivo de classe em uma pasta separada, por exemplo, CustomCode \\ *YourDomainClass*. cs.

     Certifique-se de que o namespace seja o mesmo que o código gerado.

7. No arquivo de classe, escreva uma implementação parcial da classe de domínio. Na classe, escreva uma definição para o método ausente `Get` que se assemelha ao exemplo a seguir:

    ```
    namespace Company.FamilyTree
    {  public partial class Person
       {  int GetAgeValue()
          { return System.DateTime.Today.Year - this.BirthYear; }
    }  }
    ```

8. Se você definir o **tipo** para **armazenamento personalizado**, também precisará fornecer um `Set` método. Por exemplo:

    ```
    void SetAgeValue(int value)
    { if (!Store.InUndoRedoOrRollback)
        this.BirthYear =
            System.DateTime.Today.Year - value; }
    ```

     Seu código não deve definir valores no repositório quando `Store.InUndoRedoOrRollback` for verdadeiro. Confira [Transações e setters personalizados](#setters).

9. Compile e execute a solução.

10. Teste a propriedade. Certifique-se de tentar **desfazer** e **refazer**.

## <a name="transactions-and-custom-setters"></a><a name="setters"></a> Transações e setters personalizados
 No método set da propriedade de armazenamento personalizado, você não precisa abrir uma transação, pois o método geralmente é chamado dentro de uma transação ativa.

 No entanto, o método Set também pode ser chamado se o usuário chamar Undo ou redo, ou se uma transação estiver sendo revertida. Quando <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> é verdadeiro, o método Set deve se comportar da seguinte maneira:

- Ele não deve fazer alterações no repositório, como atribuir valores a outras propriedades de domínio. O Gerenciador de desfazer definirá seus valores.

- No entanto, ele deve atualizar todos os recursos externos, como o conteúdo do banco de dados ou do arquivo, ou objetos fora da loja. Isso garantirá que eles sejam mantidos em sincronização com os valores na loja.

  Por exemplo:

```
void SetAgeValue(int value)
{
  // If we are in Undo, no changes to Store objects:
  if (!this.Store.InUndoRedoOrRollback)
  {
    this.BirthYear = System.DateTime.Today.Year - value;
  }
  // But always update external objects:
  System.IO.File.WriteAllText(AgeFile, value);
}
```

 Para obter mais informações sobre transações, consulte [navegando e atualizando um modelo no código do programa](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Veja também

- [Navegando e atualizando um modelo no código do programa](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Propriedades das propriedades de domínio](../modeling/properties-of-domain-properties.md)
- [Como definir uma linguagem específica do domínio](../modeling/how-to-define-a-domain-specific-language.md)
