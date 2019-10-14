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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e607da01d160212eea03b1fe81dfb2fbf4ede3f6
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305688"
---
# <a name="usage-warnings"></a>Avisos de uso

Os avisos de uso dão suporte ao uso adequado do .NET.

## <a name="in-this-section"></a>Nesta seção

|Regra|{1&gt;Descrição&lt;1}|
|----------|-----------------|
|[CA1801: Examinar parâmetros não utilizados @ no__t-0|Uma assinatura de método inclui um parâmetro que não é usado no corpo do método.|
|[CA1806: Não ignore os resultados do método @ no__t-0|Um novo objeto é criado, mas nunca é usado; ou um método que cria e retorna uma nova cadeia de caracteres é chamado e a nova cadeia de caracteres jamais é usada; um método ou COM ou P/Invoke retorna um HRESULT ou um código de erro que nunca é usado.|
|[CA1816: Chame GC. SuppressFinalize corretamente @ no__t-0|Um método que é uma implementação de Dispose não chama GC. SuppressFinalize; ou um método que não é uma implementação de Dispose chama GC. SuppressFinalize; ou um método chama GC. SuppressFinalize e passa algo que não seja isso (Me no Visual Basic).|
|[CA2200: Relançar para preservar detalhes da pilha @ no__t-0|Uma exceção é lançada novamente e a exceção é especificada explicitamente na instrução throw. Se uma exceção for lançada novamente pela especificação da exceção na instrução throw, a lista de chamadas de método entre o método original que lançou a exceção e o método atual será perdida.|
|[CA2201: Não gerar tipos de exceção reservados @ no__t-0|Isso torna o erro original difícil de detectar e depurar.|
|[CA2202: Não descartar objetos várias vezes @ no__t-0|Uma implementação do método contém caminhos de código que poderiam causar várias chamadas para System.IDisposable.Dispose ou para um equivalente a Dispose (como um método Close() em alguns tipos) no mesmo objeto.|
|[CA2204: Os literais devem ser escritos corretamente @ no__t-0|Uma cadeia de caracteres literal em um corpo de método contém uma ou mais palavras não reconhecidas pela biblioteca do verificador ortográfico da Microsoft.|
|[CA2205: Usar equivalentes gerenciados da API do Win32 @ no__t-0|Um método de invocação de plataforma é definido e um método .NET com a funcionalidade equivalente está disponível.|
|[CA2207: Inicializar campos estáticos do tipo de valor embutido @ no__t-0|Um tipo de valor declara um construtor estático explícito. Para corrigir uma violação dessa regra, inicialize todos os dados estáticos quando declarados e remova o construtor estático.|
|[CA2208: Instanciar exceções de argumento corretamente @ no__t-0|For feita uma chamada para o construtor padrão (sem parâmetros) de um tipo de exceção que seja ou derive de ArgumentException, ou um argumento de cadeia de caracteres incorreto é passado para um construtor com parâmetros de um tipo de exceção que seja ou derive de ArgumentException.|
|[CA2211: Campos não constantes não devem ser visíveis @ no__t-0|Campos estáticos que não são constantes ou somente leitura não são thread-safe. O acesso a esse campo deve ser cuidadosamente controlado e requer técnicas de programação avançadas para sincronizar o acesso ao objeto de classe.|
|[CA2212: Não marcar componentes atendidos com WebMethod @ no__t-0|Um método em um tipo que herda de System. EnterpriseServices. ServicedComponent é marcado com System. Web. Services. WebMethodAttribute. Como WebMethodAttribute e um método ServicedComponent têm comportamento e requisitos conflitantes para o contexto e o fluxo de transações, o comportamento do método estará incorreto em alguns cenários.|
|[CA2213: os campos descartáveis devem ser descartados](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Um tipo que implementa System.IDisposable declara campos que são de tipos que também implementam IDisposable. O método Dispose do campo não é chamado pelo método Dispose do tipo declarante.|
|[CA2214: Não chamar métodos substituíveis em construtores @ no__t-0|Quando um construtor chama um método virtual, é possível que o construtor da instância que invoca o método não tenha sido executado.|
|[CA2215: Métodos Dispose devem chamar a classe base Dispose @ no__t-0|Se for herdado de um tipo descartável, um tipo deverá chamar o método Dispose do tipo de base em seu próprio método Dispose.|
|[CA2216: Tipos descartáveis devem declarar finalizador @ no__t-0|Um tipo que implementa System. IDisposable e tem campos que sugerem o uso de recursos não gerenciados, não implementa um finalizador, conforme descrito por Object. Finalize.|
|[CA2217: Não marque enums com FlagsAttribute @ no__t-0|Uma enumeração visível externamente é marcada com FlagsAttribute e tem um ou mais valores que não são potências de duas ou uma combinação de outros valores definidos na enumeração.|
|[CA2218: Substituir GetHashCode ao substituir é igual a @ no__t-0|GetHashCode retorna um valor, com base na instância atual, adequado para algoritmos de hash e estruturas de dados como uma tabela de hash. Dois objetos que tenham o mesmo tipo e sejam iguais devem retornar o mesmo código hash.|
|[CA2219: Não gerar exceções nas cláusulas de exceção @ no__t-0|Quando uma exceção é acionada em uma cláusula finally ou fault, a nova exceção oculta a exceção ativa. Quando uma exceção é acionada em uma cláusula de filtro, o tempo de execução captura silenciosamente a exceção. Isso torna o erro original difícil de detectar e depurar.|
|[CA2220: Os finalizadores devem chamar o finalizador de classe base @ no__t-0|A finalização deve ser propagada em toda a hierarquia de herança. Para garantir isso, os tipos devem chamar o método Finalize de classe base em seu próprio método Finalize.|
|[CA2221: Os finalizadores devem ser protegidos @ no__t-0|Os finalizadores deve usar o modificador de acesso da família.|
|[CA2222: Não diminuir a visibilidade de membro herdada @ no__t-0|Não altere o modificador de acesso para membros herdados. A alteração de um membro herdado para particular não impede que os chamadores acessem a implementação da classe base do método.|
|[CA2223: Os membros devem ser diferentes por mais do que o tipo de retorno @ no__t-0|Embora o Common Language Runtime permita o uso de tipos de retorno na diferenciação de membros outrora idênticos, este recurso não está na CLS nem é um recurso comum das linguagens de programação do .NET.|
|[CA2224: Substituir Equals no operador de sobrecarga igual a @ no__t-0|Um tipo público implementa o operador de igualdade, mas não substitui Object. Equals.|
|[CA2225: Sobrecargas de operador têm nomes alternativos @ no__t-0|Uma sobrecarga de operador foi detectada, e o método alternativo nomeado esperado não foi encontrado. O membro alternativo nomeado fornece acesso à mesma funcionalidade que o operador e é fornecido para desenvolvedores que programam em idiomas que não dão suporte a operadores sobrecarregados.|
|[CA2226: Os operadores devem ter sobrecargas simétricas @ no__t-0|Um tipo implementa o operador de igualdade ou desigualdade e não implementa o operador oposto.|
|[CA2227: As propriedades da coleção devem ser somente leitura @ no__t-0|Uma propriedade collection gravável permite que um usuário substitua a coleção por uma coleção diferente. Uma propriedade somente leitura evita que a coleção seja substituída, mas ainda permite que membros individuais sejam definidos.|
|[CA2228: Não enviar formatos de recurso não lançados @ no__t-0|Os arquivos de recursos criados usando versões de pré-lançamento do .NET podem não ser utilizáveis por versões do .NET com suporte.|
|[CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)|Para corrigir uma violação dessa regra, implemente o construtor de serialização. Para uma classe lacrada, torne o construtor particular; do contrário, deixe-o protegido.|
|[CA2230: Usar params para argumentos de variável @ no__t-0|Um tipo público ou protegido contém um método público ou protegido que usa a convenção de chamada VarArgs, em vez da palavra-chave params.|
|[CA2231: o operador de sobrecarga é igual ao substituir ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Um tipo de valor substitui `Object.Equals`, mas não implementa o operador de igualdade.|
|[CA2232: Marcar pontos de entrada de Windows Forms com STAThread @ no__t-0|STAThreadAttribute indica que o modelo de threading COM para o aplicativo é um single-threaded apartment. Esse atributo deve estar presente no ponto de entrada de qualquer aplicativo que use o Windows Forms; se ele for omitido, os componentes do Windows poderão não funcionar corretamente.|
|[CA2233: As operações não devem exceder o estouro de @ no__t-0|As operações aritméticas não devem ser executadas sem validar primeiro os operandos, para garantir que o resultado da operação não esteja fora do intervalo de valores possíveis para os tipos de dados envolvidos.|
|[CA2234: Passe objetos System. Uri em vez de cadeias de caracteres @ no__t-0|Foi feita uma chamada para um método com um parâmetro de cadeia de caracteres cujo nome contém "uri", "URI", "urn", "URN", "url" ou "URL".  O tipo declarante do método contém uma sobrecarga do método correspondente que possui um parâmetro System.Uri.|
|[CA2235: Marcar todos os campos não serializáveis](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Um campo de instância de um tipo que não seja serializável é declarado em um tipo que é serializável.|
|[CA2236: Chamar métodos de classe base em tipos ISerializable @ no__t-0|Para corrigir uma violação dessa regra, chame o método GetObjectData de tipo base ou o construtor de serialização do método de tipo derivado correspondente ou do construtor.|
|[CA2237: Marcar tipos ISerializable com SerializableAttribute @ no__t-0|Para ser reconhecido pelo Common Language Runtime como serializável, os tipos devem ser marcados com o atributo SerializableAttribute, mesmo que o tipo use uma rotina de serialização personalizada por meio da implementação da interface ISerializable.|
|[CA2238: Implementar métodos de serialização corretamente @ no__t-0|Um método que trata um evento de serialização não tem a assinatura, o tipo de retorno ou a visibilidade corretos.|
|[CA2239: Fornecer métodos de desserialização para campos opcionais @ no__t-0|Um tipo tem um campo que é marcado com o atributo System. Runtime. Serialization. OptionalFieldAttribute e o tipo não fornece métodos de manipulação de eventos de serialização.|
|[CA2240: Implementar ISerializable corretamente @ no__t-0|Para corrigir uma violação dessa regra, torne o método GetObjectData visível e substituível e verifique se todos os campos de instância estão incluídos no processo de serialização ou explicitamente marcados com o atributo nonserializadoattribute.|
|[CA2241: Forneça os argumentos corretos para os métodos de formatação @ no__t-0|O argumento de formato passado para System. String. Format não contém um item de formato que corresponde a cada argumento de objeto ou vice-versa.|
|[CA2242: Testar para NaN corretamente @ no__t-0|Essa expressão testa um valor em Single.Nan ou Double.Nan. Use Single.IsNan (único) ou Double.IsNan (duplo) para testar o valor.|
|[CA2243: Literais de cadeia de caracteres de atributo devem ser analisados corretamente @ no__t-0|O parâmetro literal da cadeia de caracteres de um atributo não é analisado corretamente para uma URL, um GUID ou uma versão.|