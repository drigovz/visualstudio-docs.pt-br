---
title: Avisos de desempenho
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.performancerules
helpviewer_keywords:
- warnings, performance
- performance warnings
- performance, warnings
- managed code analysis warnings, performance warnings
ms.assetid: e014ac3a-02e6-46d9-942c-3491dd63782f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29ace36d35b31eeb3635d06d6244ac6fe0897ec2
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305664"
---
# <a name="performance-warnings"></a>Avisos de desempenho
Os avisos de desempenho dão suporte a bibliotecas e aplicativos de alto desempenho.

## <a name="in-this-section"></a>Nesta seção

| Regra | {1&gt;Descrição&lt;1} |
| - | - |
| [CA1800: Não converter desnecessariamente @ no__t-0 | As conversões duplicadas diminui o desempenho, especialmente quando as conversões são realizadas em instruções de iteração compactas. |
| [CA1801: Examinar parâmetros não utilizados @ no__t-0 | Uma assinatura de método inclui um parâmetro que não é usado no corpo do método. |
| [CA1802: Usar literais onde @ no__t-0 apropriado | Um campo é declarado estático e somente leitura (compartilhado e ReadOnly em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) e é inicializado com um valor que é computáveis no momento da compilação. Como o valor que é atribuído ao campo de destino é computável no tempo de compilação, altere a declaração para const (Const em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) para que o valor é calculado em tempo de compilação em vez de em tempo de execução de campo. |
| [CA1804: Remover locais não utilizados @ no__t-0 | As variáveis locais não utilizadas e as atribuições desnecessárias aumentam o tamanho de um assembly e diminuem o desempenho. |
| [CA1806: Não ignore os resultados do método @ no__t-0 | Um novo objeto é criado, mas nunca usado, ou um método que cria e retorna uma nova cadeia de caracteres é chamado e a nova cadeia de caracteres nunca é usada ou um método Component Object Model (COM) ou P/Invoke Retorna um HRESULT ou um código de erro que nunca é usado. |
| [CA1809: Evite locais em excesso no @ no__t-0 | Uma otimização de desempenho comum é armazenar um valor em um registro de processador, em vez da memória, algo conhecido como "registro do valor".  Para aumentar a chance de que todas as variáveis locais sejam cancelado, limite o número de variáveis locais a 64. |
| [CA1810: Inicialize os campos estáticos do tipo de referência em linha @ no__t-0 | Quando um tipo declara um construtor estático explícito, o compilador JIT (just-in-time) adiciona uma verificação a cada método estático e construtor de instância do tipo para garantir que o construtor estático tenha sido chamado anteriormente. As verificações de construtor estático podem diminuir o desempenho. |
| [CA1811: Evite código particular não chamado @ no__t-0 | Um membro privado ou interno (no nível do assembly) não tem chamadores no assembly, ele não é invocado pelo Common Language Runtime e não é invocado por um delegado. |
| [CA1812: Evite classes internas não instanciadas @ no__t-0 | Uma instância de um tipo no nível de assembly não é criada pelo código no assembly. |
| [CA1813: Evitar atributos não lacrados @ no__t-0 | O .NET fornece métodos para recuperar atributos personalizados. Por padrão, esses métodos pesquisam a hierarquia de herança do atributo. A validação do atributo elimina a pesquisa na hierarquia de herança e pode melhorar o desempenho. |
| [CA1814: Prefira matrizes denteadas sobre multidimensional @ no__t-0 | Uma matriz denteada é uma matriz cujos elementos são matrizes. As matrizes que compõem os elementos podem ser de tamanhos diferentes, o que pode resultar em menos espaço desperdiçado para alguns conjuntos de dados. |
| [CA1815: Substituir equals e operador equals em tipos de valor](../code-quality/ca1815.md) | Para tipos de valor, a implementação herdada de Equals usa a biblioteca Reflection e compara o conteúdo de todos os campos. Reflection é computacionalmente cara, e pode ser desnecessário comparar a igualdade de cada campo. Se você espera que os usuários comparem ou classifiquem instâncias, ou usem instâncias como chaves de tabela de hash, o tipo de valor deverá implementar Equals. |
| [CA1816: Chame GC. SuppressFinalize corretamente @ no__t-0 | Um método que é uma implementação de Dispose não chama GC. SuppressFinalize, ou um método que não é uma implementação de Dispose chama GC. SuppressFinalize, ou um método chama GC. SuppressFinalize e passa algo diferente deste (eu em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). |
| [CA1819: Propriedades não devem retornar matrizes @ no__t-0 | As matrizes retornadas por propriedades não são protegidas por gravação, mesmo que a propriedade seja somente leitura. Para manter a matriz à prova de adulteração, a propriedade deve retornar uma cópia da matriz. Normalmente, os usuários não compreenderão as implicações adversas no desempenho de chamar uma propriedade assim. |
| [CA1820: Teste para cadeias de caracteres vazias usando o comprimento da cadeia @ no__t-0 | A comparação de cadeias de caracteres usando-se a propriedade String.Length ou o método String.IsNullOrEmpty é significativamente mais rápida do que o uso de Equals. |
| [CA1821: remova os finalizadores vazios](../code-quality/ca1821.md) | Sempre que possível, evite finalizadores por conta da sobrecarga adicional no desempenho envolvida no acompanhamento do tempo de vida do objeto. Um finalizador vazio incorre em sobrecarga adicional sem nenhum benefício. |
| [CA1822: Marcar Membros como estáticos @ no__t-0 | Os membros que não acessam dados da instância ou os métodos da instância de chamada podem ser marcados como estáticos (Shared no [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Depois que você marcar os métodos como estáticos, o compilador emitirá sites de chamada não virtuais para esses membros. Isso pode proporcionar um ganho de desempenho mensurável para o código sensível ao desempenho. |
| [CA1823: Evite campos particulares não utilizados @ no__t-0 | Foram detectados campos particulares que aparentemente não são acessados no assembly. |
| [CA1824: Marcar assemblies com NeutralResourcesLanguageAttribute @ no__t-0 | O atributo NeutralResourcesLanguage informa o ResourceManager da linguagem que foi usada para exibir os recursos de uma cultura neutra para um assembly. Isso melhora o desempenho da pesquisa para o primeiro recurso carregado e pode reduzir o conjunto de trabalho. |
| [CA1825: Evitar alocações de matriz de comprimento zero @ no__t-0 | A inicialização de uma matriz de comprimento zero leva à alocação de memória desnecessária. Em vez disso, use a instância de matriz vazia estaticamente alocada chamando <xref:System.Array.Empty%2A?displayProperty=nameWithType>. A alocação de memória é compartilhada entre todas as invocações desse método. |
