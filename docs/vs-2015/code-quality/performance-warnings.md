---
title: Avisos de desempenho | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.performancerules
helpviewer_keywords:
- warnings, performance
- performance warnings
- performance, warnings
- managed code analysis warnings, performance warnings
ms.assetid: e014ac3a-02e6-46d9-942c-3491dd63782f
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9f1b8ae5f4133605bd6488baa715a451467237f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72608717"
---
# <a name="performance-warnings"></a>Avisos de desempenho
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os avisos de desempenho dão suporte a bibliotecas e aplicativos de alto desempenho.

## <a name="in-this-section"></a>Nesta seção

|Regra|Descrição|
|----------|-----------------|
|[CA1800: Não converta sem necessidade](../code-quality/ca1800-do-not-cast-unnecessarily.md)|As conversões duplicadas diminui o desempenho, especialmente quando as conversões são realizadas em instruções de iteração compactas.|
|[CA1801: Examinar parâmetros não utilizados](../code-quality/ca1801-review-unused-parameters.md)|Uma assinatura de método inclui um parâmetro que não é usado no corpo do método.|
|[CA1802: Usar literais quando apropriado](../code-quality/ca1802-use-literals-where-appropriate.md)|Um campo é declarado estático e somente leitura (compartilhado e ReadOnly em [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) e é inicializado com um valor que é computáveis no momento da compilação. Como o valor atribuído ao campo de destino é computáveis em tempo de compilação, altere a declaração para um campo const (const in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) para que o valor seja calculado em tempo de compilação em vez de em tempo de execução.|
|[CA1804: Remover locais não utilizados](../code-quality/ca1804-remove-unused-locals.md)|As variáveis locais não utilizadas e as atribuições desnecessárias aumentam o tamanho de um assembly e diminuem o desempenho.|
|[CA1806: Não ignorar resultados do método](../code-quality/ca1806-do-not-ignore-method-results.md)|Um novo objeto é criado, mas nunca usado, ou um método que cria e retorna uma nova cadeia de caracteres é chamado e a nova cadeia de caracteres nunca é usada ou um método Component Object Model (COM) ou P/Invoke Retorna um HRESULT ou um código de erro que nunca é usado.|
|[CA1809: Evitar locais excessivos](../code-quality/ca1809-avoid-excessive-locals.md)|Uma otimização de desempenho comum é armazenar um valor em um registro de processador, em vez da memória, algo conhecido como "registro do valor".  Para aumentar a possibilidade de que o registro de todas as variáveis locais seja cancelado, limite o número de variáveis locais a 64.|
|[CA1810: Inicializar campos estáticos de tipo de referência em linha](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|Quando um tipo declara um construtor estático explícito, o compilador JIT (just-in-time) adiciona uma verificação a cada método estático e construtor de instância do tipo para garantir que o construtor estático tenha sido chamado anteriormente. As verificações de construtor estático podem diminuir o desempenho.|
|[CA1811: Evitar código particular não chamado](../code-quality/ca1811-avoid-uncalled-private-code.md)|Um membro privado ou interno (no nível do assembly) não tem chamadores no assembly, ele não é invocado pelo Common Language Runtime e não é invocado por um delegado.|
|[CA1812: Evitar classes internas sem instâncias](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)|Uma instância de um tipo no nível de assembly não é criada pelo código no assembly.|
|[CA1813: Evitar atributos não selados](../code-quality/ca1813-avoid-unsealed-attributes.md)|A biblioteca de classes do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] fornece métodos para recuperar atributos personalizados. Por padrão, esses métodos pesquisam a hierarquia de herança do atributo. A validação do atributo elimina a pesquisa na hierarquia de herança e pode melhorar o desempenho.|
|[CA1814: Preferir matrizes denteadas a matrizes multidimensionais](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|Uma matriz denteada é uma matriz cujos elementos são matrizes. As matrizes que compõem os elementos podem ser de tamanhos diferentes, o que pode resultar em menos espaço desperdiçado para alguns conjuntos de dados.|
|[CA1815: Substituir equals e o operador equals em tipos de valor](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)|Para tipos de valor, a implementação herdada de Equals usa a biblioteca Reflection e compara o conteúdo de todos os campos. Reflection é computacionalmente cara, e pode ser desnecessário comparar a igualdade de cada campo. Se você espera que os usuários comparem ou classifiquem instâncias, ou usem instâncias como chaves de tabela de hash, o tipo de valor deverá implementar Equals.|
|[CA1816: Chamar GC.SuppressFinalize corretamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Um método que é uma implementação de Dispose não chama GC. SuppressFinalize, ou um método que não é uma implementação de Dispose chama GC. SuppressFinalize, ou um método chama GC. SuppressFinalize e passa algo diferente deste (eu em [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ).|
|[CA1819: Propriedades não devem retornar matrizes](../code-quality/ca1819-properties-should-not-return-arrays.md)|As matrizes retornadas por propriedades não são protegidas por gravação, mesmo que a propriedade seja somente leitura. Para manter a matriz à prova de adulteração, a propriedade deve retornar uma cópia da matriz. Normalmente, os usuários não compreenderão as implicações adversas no desempenho de chamar uma propriedade assim.|
|[CA1820: Testar para verificar se há cadeias de caracteres vazias usando o tamanho da cadeia de caracteres](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|A comparação de cadeias de caracteres usando-se a propriedade String.Length ou o método String.IsNullOrEmpty é significativamente mais rápida do que o uso de Equals.|
|[CA1821: Remover finalizadores vazios](../code-quality/ca1821-remove-empty-finalizers.md)|Sempre que possível, evite finalizadores por conta da sobrecarga adicional no desempenho envolvida no acompanhamento do tempo de vida do objeto. Um finalizador vazio incorre em sobrecarga adicional sem nenhum benefício.|
|[CA1822: Marcar membros como estáticos](../code-quality/ca1822-mark-members-as-static.md)|Os membros que não acessam dados da instância ou os métodos da instância de chamada podem ser marcados como estáticos (Shared no [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]). Depois que você marcar os métodos como estáticos, o compilador emitirá sites de chamada não virtuais para esses membros. Isso pode proporcionar um ganho de desempenho mensurável para o código sensível ao desempenho.|
|[CA1823: Evitar campos particulares não utilizados](../code-quality/ca1823-avoid-unused-private-fields.md)|Foram detectados campos particulares que aparentemente não são acessados no assembly.|
|[CA1824: Marque assemblies com NeutralResourcesLanguageAttribute](../code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md)|O atributo NeutralResourcesLanguage informa o ResourceManager da linguagem que foi usada para exibir os recursos de uma cultura neutra para um assembly. Isso melhora o desempenho da pesquisa para o primeiro recurso carregado e pode reduzir o conjunto de trabalho.|
