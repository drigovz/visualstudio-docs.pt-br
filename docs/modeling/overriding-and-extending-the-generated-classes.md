---
title: Substituindo e estendendo as classes geradas
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, providing overridable classes
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3374f67f4fba11543e3dbbca47fef621dd2e714
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595885"
---
# <a name="override-and-extend-the-generated-classes"></a>Substituir e estender as classes geradas

Sua definição de DSL é uma plataforma na qual você pode criar um conjunto avançado de ferramentas baseadas em uma linguagem específica de domínio. Muitas extensões e adaptações podem ser feitas substituindo e estendendo as classes que são geradas a partir da definição de DSL. Essas classes incluem não apenas as classes de domínio que você definiu explicitamente no diagrama de definição de DSL, mas também outras classes que definem a caixa de ferramentas, o Explorer, a serialização e assim por diante.

## <a name="extensibility-mechanisms"></a>Mecanismos de extensibilidade

Vários mecanismos são fornecidos para permitir que você estenda o código gerado.

### <a name="override-methods-in-a-partial-class"></a>Substituir métodos em uma classe parcial

As definições de classe parcial permitem que uma classe seja definida em mais de um lugar. Isso permite que você separe o código gerado do código que você escreve por conta própria. No código escrito manualmente, você pode substituir classes herdadas pelo código gerado.

Por exemplo, se, em sua definição de DSL, você definir uma classe de domínio denominada `Book`, poderá escrever um código personalizado que adiciona métodos de substituição:

```csharp
public partial class Book
{
   protected override void OnDeleting()
   {
      MessageBox.Show("Deleting book " + this.Title);
      base.OnDeleting();
   }
}
```

> [!NOTE]
> Para substituir métodos em uma classe gerada, sempre grave seu código em um arquivo que está separado dos arquivos gerados. Normalmente, o arquivo está contido em uma pasta chamada CustomCode. Se você fizer alterações no código gerado, elas serão perdidas quando você regenerar o código da definição de DSL.

Para descobrir quais métodos você pode substituir, digite **override** na classe, seguida por um espaço. A dica de ferramenta do IntelliSense informará quais métodos podem ser substituídos.

### <a name="double-derived-classes"></a>Classes derivadas de duas vezes

A maioria dos métodos em classes geradas é herdada de um conjunto fixo de classes nos namespaces de modelagem. No entanto, alguns métodos são definidos no código gerado. Normalmente, isso significa que você não pode substituí-los; Não é possível substituir em uma classe parcial os métodos que são definidos em outra definição parcial da mesma classe.

No entanto, você pode substituir esses métodos definindo o sinalizador de **gerações derivadas duplas** para a classe de domínio. Isso faz com que duas classes sejam geradas, uma sendo uma classe base abstrata da outra. Todas as definições de método e Propriedade estão na classe base, e somente o Construtor está na classe derivada.

Por exemplo, no exemplo de biblioteca. DSL, a classe de domínio `CirculationBook` tem a propriedade `Generates``Double Derived` definida como `true`. O código gerado para essa classe de domínio contém duas classes:

- `CirculationBookBase`, que é um abstrato e que contém todos os métodos e propriedades.

- `CirculationBook`, que é derivado de `CirculationBookBase`. Ele está vazio, exceto para seus construtores.

Para substituir qualquer método, você cria uma definição parcial da classe derivada, como `CirculationBook`. Você pode substituir os métodos gerados e os métodos herdados da estrutura de modelagem.

Você pode usar esse método com todos os tipos de elemento, incluindo elementos de modelo, relações, formas, diagramas e conectores. Você também pode substituir métodos de outras classes geradas. Algumas classes geradas, como ToolboxHelper, são sempre derivadas de duas vezes.

### <a name="custom-constructors"></a>Construtores personalizados

Não é possível substituir um construtor. Mesmo em classes derivadas de Double, o construtor deve estar na classe derivada.

Se você quiser fornecer seu próprio construtor, poderá fazer isso definindo `Has Custom Constructor` para a classe de domínio na definição de DSL. Quando você clica em **transformar todos os modelos**, o código gerado não inclui um construtor para essa classe. Incluirá uma chamada para o Construtor ausente. Isso causa um relatório de erros quando você cria a solução. Clique duas vezes no relatório de erros para ver um comentário no código gerado que explica o que você deve fornecer.

Escreva uma definição de classe parcial em um arquivo separado dos arquivos gerados e forneça o construtor.

### <a name="flagged-extension-points"></a>Pontos de extensão sinalizados

Um ponto de extensão sinalizado é um local na definição de DSL, onde você pode definir uma propriedade ou uma caixa de seleção para indicar que fornecerá um método personalizado. Os construtores personalizados são um exemplo. Outros exemplos incluem a definição da `Kind` de uma propriedade de domínio para o armazenamento calculado ou personalizado ou a definição do sinalizador **é personalizado** em um construtor de conexões.

Em cada caso, quando você define o sinalizador e gera novamente o código, ocorrerá um erro de compilação. Clique duas vezes no erro para ver um comentário que explica o que você precisa fornecer.

### <a name="rules"></a>Regras

O Gerenciador de transações permite que você defina regras que são executadas antes do final de uma transação na qual um evento designado ocorreu, como uma alteração em uma propriedade. Normalmente, as regras são usadas para manter sincronização entre elementos diferentes na loja. Por exemplo, as regras são usadas para garantir que o diagrama exiba o estado atual do modelo.

As regras são definidas em uma base por classe, para que você não precise ter um código que registre a regra para cada objeto. Para obter mais informações, consulte [propagam alterações dentro do modelo de regras](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="store-events"></a>Armazenar eventos

O repositório de modelagem fornece um mecanismo de eventos que você pode usar para escutar tipos específicos de alteração na loja, incluindo adição e exclusão de elementos, alterações em valores de propriedade e assim por diante. Os manipuladores de eventos são chamados após o fechamento da transação na qual as alterações foram feitas. Normalmente, esses eventos são usados para atualizar recursos fora do repositório.

### <a name="net-events"></a>Eventos .NET

Você pode assinar alguns eventos em formas. Por exemplo, você pode ouvir cliques do mouse em uma forma. Você precisa escrever um código que assine o evento para cada objeto. Esse código pode ser escrito em uma substituição de InitializeInstanceResources ().

Alguns eventos são gerados em ShapeFields, que são usados para desenhar decoradores em uma forma. Para obter um exemplo, consulte [como interceptar um clique em uma forma ou decorador](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).

Esses eventos geralmente não ocorrem dentro de uma transação. Você deve criar uma transação se quiser fazer alterações no repositório.
