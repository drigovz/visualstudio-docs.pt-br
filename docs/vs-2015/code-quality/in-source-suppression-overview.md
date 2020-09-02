---
title: Visão geral da supressão de origem | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: 42
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 63d405b0e62735c0c1e3d7bb716ea2db29bc19fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651568"
---
# <a name="in-source-suppression-overview"></a>Visão geral de supressão na origem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A supressão na origem é a capacidade de suprimir ou ignorar violações de análise de código em código gerenciado adicionando o atributo **SuppressMessage** aos segmentos de código que causam as violações. O atributo **SuppressMessage** é um atributo condicional que é incluído nos metadados de Il do assembly de código gerenciado somente se o símbolo de compilação de CODE_ANALYSIS for definido no momento da compilação.

 Em C++/CLI, use as macros CA_SUPPRESS_MESSAGE ou CA_GLOBAL_SUPPRESS_MESSAGE no arquivo de cabeçalho para adicionar o atributo.

 Você não deve usar supressões na origem em builds de versão para evitar o envio acidental dos metadados de supressão na origem. Devido ao custo de processamento da supressão na origem, o desempenho do seu aplicativo também pode ser degradado incluindo os metadados de supressão na origem.

> [!NOTE]
> Você não precisa codificar manualmente esses atributos. Para obter mais informações, consulte [como: suprimir avisos usando o item de menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md). O item de menu não está disponível para o código C++.

## <a name="suppressmessage-attribute"></a>Atributo SuppressMessage
 Quando você clica com o botão direito do mouse em um aviso de análise de código na **lista de erros** e clica em **suprimir mensagem (ns)**, um atributo **SuppressMessage** é adicionado no código ou no arquivo de supressões global do projeto.

 O atributo **SuppressMessage** tem o seguinte formato:

```vb
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]

```

 [C++]

```
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")

```

 Sendo que:

- **Categoria da regra** – a categoria na qual a regra é definida. Para obter mais informações sobre categorias de regra de análise de código, consulte [análise de código para avisos de código gerenciado](../code-quality/code-analysis-for-managed-code-warnings.md).

- **ID da regra** – o identificador da regra. O suporte inclui um nome curto e longo para o identificador de regra. O nome curto é CAXXXX; o nome longo é CAXXXX: FriendlyTypeName.

- **Justificação** – o texto que é usado para documentar o motivo da supressão da mensagem.

- **ID da mensagem** -identificador exclusivo de um problema para cada mensagem.

- **Escopo** -o destino no qual o aviso está sendo suprimido. Se o destino não for especificado, ele será definido como o destino do atributo. Os escopos com suporte incluem o seguinte:

  - Módulo

  - Namespace

  - Recurso

  - Tipo

  - Membro

- **Target** -um identificador que é usado para especificar o destino no qual o aviso está sendo suprimido. Ele deve conter um nome de item totalmente qualificado.

## <a name="suppressmessage-usage"></a>Uso de SuppressMessage
 Os avisos de análise de código são suprimidos no nível ao qual uma instância do atributo **SuppressMessage** é aplicada. A finalidade disso é acoplar rigidamente as informações de supressão ao código em que ocorre a violação.

 A forma geral de supressão inclui a categoria de regra e um identificador de regra que contém uma representação opcional legível do nome da regra. Por exemplo,

 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

 Se houver motivos estritos de desempenho para minimizar metadados de supressão na origem, o próprio nome da regra poderá ser deixado fora. A categoria de regra e sua ID de regra juntos constituem um identificador de regra suficientemente exclusivo. Por exemplo,

 `[SuppressMessage("Microsoft.Design", "CA1039")]`

 Esse formato não é recomendado devido a problemas de manutenção.

## <a name="suppressing-multiple-violations-within-a-method-body"></a>Suprimindo várias violações dentro de um corpo de método
 Os atributos só podem ser aplicados a um método e não podem ser inseridos no corpo do método. No entanto, você pode especificar o identificador como a ID da mensagem para distinguir várias ocorrências de uma violação dentro de um método.

 [!code-cpp[InSourceSuppression#1](../snippets/cpp/VS_Snippets_CodeAnalysis/InSourceSuppression/cpp/insourcesuppression.cpp#1)]
 [!code-csharp[InSourceSuppression#1](../snippets/csharp/VS_Snippets_CodeAnalysis/InSourceSuppression/cs/InSourceSuppression.cs#1)]
 [!code-vb[InSourceSuppression#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/InSourceSuppression/vb/InSourceSuppression.vb#1)]

## <a name="generated-code"></a>Código gerado
 Compiladores de código gerenciado e algumas ferramentas de terceiros geram código para facilitar o desenvolvimento rápido de código. O código gerado pelo compilador que aparece em arquivos de origem geralmente é marcado com o atributo **GeneratedCodeAttribute** .

 Você pode escolher se deseja suprimir avisos de análise de código e erros de código gerado. Para obter informações sobre como suprimir esses avisos e erros, consulte [como suprimir avisos para código gerado](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

 Observe que a análise de código ignora o **GeneratedCodeAttribute** quando ele é aplicado a um assembly inteiro ou a um único parâmetro. Essas situações raramente ocorrem.

## <a name="global-level-suppressions"></a>Supressões de nível global
 A ferramenta de análise de código gerenciado examina os atributos **SuppressMessage** que são aplicados no nível de assembly, módulo, tipo, membro ou parâmetro. Ele também dispara violações em relação a recursos e namespaces. Essas violações devem ser aplicadas no nível global e têm escopo e destino. Por exemplo, a seguinte mensagem suprime uma violação de namespace:

 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Quando você suprimi um aviso com escopo de namespace, ele suprime o aviso em relação ao próprio namespace. Ele não elimina o aviso em relação aos tipos no namespace.

 Qualquer supressão pode ser expressa especificando um escopo explícito. Essas supressões devem residir no nível global. Não é possível especificar a supressão de nível de membro decorando um tipo.

 As supressões de nível global são a única maneira de suprimir mensagens que se referem ao código gerado pelo compilador que não é mapeado para a fonte de usuário fornecida explicitamente. Por exemplo, o código a seguir suprime uma violação em relação a um Construtor emitido pelo compilador:

 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> O destino sempre contém o nome do item totalmente qualificado.

## <a name="global-suppression-file"></a>Arquivo de supressão global
 O arquivo de supressão global mantém supressões que são supressões de nível global ou supressões que não especificam um destino. Por exemplo, as supressões para violações de nível de assembly são armazenadas nesse arquivo. Além disso, algumas supressões ASP.NET são armazenadas nesse arquivo porque as configurações de nível de projeto não estão disponíveis para o código por trás de um formulário. Uma supressão global é criada e adicionada ao projeto na primeira vez que você seleciona a opção **no arquivo de supressão do projeto** do comando **suprimir mensagem (s)** na janela lista de erros. Para obter mais informações, consulte [como: suprimir avisos usando o item de menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).

## <a name="see-also"></a>Consulte Também
 <xref:System.Diagnostics.CodeAnalysis>
