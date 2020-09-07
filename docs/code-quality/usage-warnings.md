---
title: Avisos de uso
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.usagerules
helpviewer_keywords:
- warnings, usage
- managed code analysis warnings, usage warnings
- usage warnings
ms.assetid: fe7dc2a3-289d-4bf7-a1e4-0947a81287c4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dd2f5919b0f48290ecc14cf71295e2af0bac4748
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509712"
---
# <a name="usage-warnings"></a>Avisos de uso

Os avisos de uso dão suporte ao uso adequado do .NET.

## <a name="in-this-section"></a>Nesta seção

|Regra|Descrição|
|----------|-----------------|
|[CA1801: Examinar parâmetros não utilizados](../code-quality/ca1801.md)|Uma assinatura de método inclui um parâmetro que não é usado no corpo do método.|
|[CA1816: Chamar GC.SuppressFinalize corretamente](../code-quality/ca1816.md)|Um método que é uma implementação de Dispose não chama GC.SuppressFinalize; ou um método que não é uma implementação de Dispose chama GC.SuppressFinalize; ou um método chama GC.SuppressFinalize e passa algo que não seja isso (Me no Visual Basic).|
|[CA2200: Relançar para preservar detalhes da pilha](../code-quality/ca2200.md)|Uma exceção é lançada novamente e a exceção é especificada explicitamente na instrução throw. Se uma exceção for lançada novamente pela especificação da exceção na instrução throw, a lista de chamadas de método entre o método original que lançou a exceção e o método atual será perdida.|
|[CA2201: Não acionar tipos de exceção reservados](../code-quality/ca2201.md)|Isso torna o erro original difícil de detectar e depurar.|
|[CA2202: Não descartar objetos várias vezes](../code-quality/ca2202.md)|Uma implementação do método contém caminhos de código que poderiam causar várias chamadas para System.IDisposable.Dispose ou para um equivalente a Dispose (como um método Close() em alguns tipos) no mesmo objeto.|
|[CA2207: Inicializar campos estáticos de tipo de valor em linha](../code-quality/ca2207.md)|Um tipo de valor declara um construtor estático explícito. Para corrigir uma violação dessa regra, inicialize todos os dados estáticos quando declarados e remova o construtor estático.|
|[CA2208: Criar instância de exceções de argumento corretamente](../code-quality/ca2208.md)|For feita uma chamada para o construtor padrão (sem parâmetros) de um tipo de exceção que seja ou derive de ArgumentException, ou um argumento de cadeia de caracteres incorreto é passado para um construtor com parâmetros de um tipo de exceção que seja ou derive de ArgumentException.|
|[CA2211: Campos não constantes não devem ser visíveis](../code-quality/ca2211.md)|Campos estáticos que não são constantes ou somente leitura não são thread-safe. O acesso a esse campo deve ser cuidadosamente controlado e requer técnicas de programação avançadas para sincronizar o acesso ao objeto de classe.|
|[CA2213: Campos descartáveis devem ser descartados](../code-quality/ca2213.md)|Um tipo que implementa System.IDisposable declara campos que são de tipos que também implementam IDisposable. O método Dispose do campo não é chamado pelo método Dispose do tipo declarante.|
|[CA2214: Não chamar métodos substituíveis em construtores](../code-quality/ca2214.md)|Quando um construtor chama um método virtual, é possível que o construtor da instância que invoca o método não tenha sido executado.|
|[CA2215: Métodos Dispose devem chamar o descarte da classe base](../code-quality/ca2215.md)|Se for herdado de um tipo descartável, um tipo deverá chamar o método Dispose do tipo de base em seu próprio método Dispose.|
|[CA2216: Tipos descartáveis devem declarar o finalizador](../code-quality/ca2216.md)|Um tipo que implementa System. IDisposable e tem campos que sugerem o uso de recursos não gerenciados, não implementa um finalizador, conforme descrito por Object. Finalize.|
|[CA2217: Não marcar enumerações com FlagsAttribute](../code-quality/ca2217.md)|Uma enumeração visível externamente é marcada com FlagsAttribute e tem um ou mais valores que não são potências de duas ou uma combinação de outros valores definidos na enumeração.|
|[CA2219: Não acionar exceções em cláusulas de exceção](../code-quality/ca2219.md)|Quando uma exceção é acionada em uma cláusula finally ou fault, a nova exceção oculta a exceção ativa. Quando uma exceção é acionada em uma cláusula de filtro, o tempo de execução captura silenciosamente a exceção. Isso torna o erro original difícil de detectar e depurar.|
|[CA2225: Sobrecargas de operador têm alternativas nomeadas](../code-quality/ca2225.md)|Uma sobrecarga de operador foi detectada, e o método alternativo nomeado esperado não foi encontrado. O membro alternativo nomeado fornece acesso à mesma funcionalidade que o operador e é fornecido para desenvolvedores que programam em idiomas que não dão suporte a operadores sobrecarregados.|
|[CA2226: Operadores devem ter sobrecargas simétricas](../code-quality/ca2226.md)|Um tipo implementa o operador de igualdade ou desigualdade e não implementa o operador oposto.|
|[CA2227: Propriedades de coleção devem ser somente leitura](../code-quality/ca2227.md)|Uma propriedade collection gravável permite que um usuário substitua a coleção por uma coleção diferente. Uma propriedade somente leitura evita que a coleção seja substituída, mas ainda permite que membros individuais sejam definidos.|
|[CA2229: Implementar construtores de serialização](../code-quality/ca2229.md)|Para corrigir uma violação dessa regra, implemente o construtor de serialização. Para uma classe lacrada, torne o construtor particular; do contrário, deixe-o protegido.|
|[CA2231: Sobrecarregar operador equals ao substituir ValueType.Equals](../code-quality/ca2231.md)|Um tipo de valor substitui `Object.Equals` mas não implementa o operador de igualdade.|
|[CA2232: Marcar pontos de entrada do Windows Forms com STAThread](../code-quality/ca2232.md)|STAThreadAttribute indica que o modelo de threading COM para o aplicativo é um single-threaded apartment. Esse atributo deve estar presente no ponto de entrada de qualquer aplicativo que use o Windows Forms; se ele for omitido, os componentes do Windows poderão não funcionar corretamente.|
|[CA2233: As operações não devem estourar](../code-quality/ca2233.md)|As operações aritméticas não devem ser executadas sem validar primeiro os operandos, para garantir que o resultado da operação não esteja fora do intervalo de valores possíveis para os tipos de dados envolvidos.|
|[CA2234: Passar objetos System.Uri em vez de cadeias de caracteres](../code-quality/ca2234.md)|Foi feita uma chamada para um método com um parâmetro de cadeia de caracteres cujo nome contém "uri", "URI", "urn", "URN", "url" ou "URL".  O tipo declarante do método contém uma sobrecarga do método correspondente que possui um parâmetro System.Uri.|
|[CA2235: Marcar todos os campos não serializáveis](../code-quality/ca2235.md)|Um campo de instância de um tipo que não seja serializável é declarado em um tipo que é serializável.|
|[CA2236: Chamar métodos da classe base em tipos ISerializable](../code-quality/ca2236.md)|Para corrigir uma violação dessa regra, chame o método GetObjectData de tipo base ou o construtor de serialização do método de tipo derivado correspondente ou do construtor.|
|[CA2237: Marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237.md)|Para ser reconhecido pelo Common Language Runtime como serializável, os tipos devem ser marcados com o atributo SerializableAttribute, mesmo que o tipo use uma rotina de serialização personalizada por meio da implementação da interface ISerializable.|
|[CA2238: Implementar métodos de serialização corretamente](../code-quality/ca2238.md)|Um método que trata um evento de serialização não tem a assinatura, o tipo de retorno ou a visibilidade corretos.|
|[CA2239: Fornecer métodos de desserialização para campos opcionais](../code-quality/ca2239.md)|Um tipo tem um campo que é marcado com o atributo System. Runtime. Serialization. OptionalFieldAttribute e o tipo não fornece métodos de manipulação de eventos de serialização.|
|[CA2240: Implementar ISerializable corretamente](../code-quality/ca2240.md)|Para corrigir uma violação dessa regra, torne o método GetObjectData visível e substituível e verifique se todos os campos de instância estão incluídos no processo de serialização ou explicitamente marcados com o atributo nonserializadoattribute.|
|[CA2241: Fornecer argumentos corretos para métodos de formatação](../code-quality/ca2241.md)|O argumento de formato passado para System. String. Format não contém um item de formato que corresponde a cada argumento de objeto ou vice-versa.|
|[CA2242: Testar para NaN corretamente](../code-quality/ca2242.md)|Essa expressão testa um valor em Single.Nan ou Double.Nan. Use Single.IsNan (único) ou Double.IsNan (duplo) para testar o valor.|
|[CA2243: Literais de cadeias de caracteres de atributo devem ser analisados corretamente](../code-quality/ca2243.md)|O parâmetro literal da cadeia de caracteres de um atributo não é analisado corretamente para uma URL, um GUID ou uma versão.|
|[CA2244: Não duplicar inicializações de elementos indexados](../code-quality/ca2244.md)|Um inicializador de objeto tem mais de um inicializador de elemento indexado com o mesmo índice de constante. Todos, exceto o último inicializador, são redundantes.|
|[CA2245: Não atribuir uma propriedade a si mesma](../code-quality/ca2245.md)|Uma propriedade foi acidentalmente atribuída a ela mesma.|
|[CA2246: Não designar um símbolo e o membro dele na mesma instrução](../code-quality/ca2246.md)|Não é recomendável atribuir um símbolo e seu membro, ou seja, um campo ou uma propriedade, na mesma instrução. Não fica claro se o acesso de membro foi projetado para usar o valor antigo do símbolo antes da atribuição ou o novo valor da atribuição nesta instrução.|
|[CA2247: O argumento passado para o construtor TaskCompletionSource deve ser a enumeração TaskCreationOptions em vez da enumeração TaskContinuationOptions](../code-quality/ca2246.md)|TaskCompletionSource tem construtores que usam TaskCreationOptions que controlam a tarefa subjacente e construtores que assumem o estado do objeto armazenado na tarefa.  Passar acidentalmente um TaskContinuationOptions em vez de um TaskCreationOptions resultará na chamada que trata as opções como estado.|
|[CA2248: forneça o argumento ' Enum ' correto para ' Enum. HasFlag '](../code-quality/ca2248.md)|O tipo de enumeração passado como um argumento para a `HasFlag` chamada do método é diferente do tipo de enumeração de chamada.|
|[CA2249: Considerar o uso de String.Contains em vez de String.IndexOf](../code-quality/ca2249.md)|Chamadas para `string.IndexOf` onde o resultado é usado para verificar a presença ou a ausência de uma subcadeia de caracteres podem ser substituídas por `string.Contains` .|
