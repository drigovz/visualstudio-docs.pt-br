---
title: Avisos de uso | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.usagerules
helpviewer_keywords:
- warnings, usage
- managed code analysis warnings, usage warnings
- usage warnings
ms.assetid: fe7dc2a3-289d-4bf7-a1e4-0947a81287c4
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bd1e993723d3ef1779eb3a23e19fedd081b6a6d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603521"
---
# <a name="usage-warnings"></a>Avisos de uso
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os avisos de uso dão suporte ao uso adequado do .NET Framework.

## <a name="in-this-section"></a>Nesta seção

|Regra|Descrição|
|----------|-----------------|
|[CA1801: Examinar parâmetros não utilizados](../code-quality/ca1801-review-unused-parameters.md)|Uma assinatura de método inclui um parâmetro que não é usado no corpo do método.|
|[CA1806: Não ignorar resultados do método](../code-quality/ca1806-do-not-ignore-method-results.md)|Um novo objeto é criado, mas nunca é usado; ou um método que cria e retorna uma nova cadeia de caracteres é chamado e a nova cadeia de caracteres jamais é usada; um método ou COM ou P/Invoke retorna um HRESULT ou um código de erro que nunca é usado.|
|[CA1816: Chamar GC.SuppressFinalize corretamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Um método que é uma implementação de Dispose não chama GC.SuppressFinalize; ou um método que não é uma implementação de Dispose chama GC.SuppressFinalize; ou um método chama GC.SuppressFinalize e passa algo que não seja isso (Me no Visual Basic).|
|[CA2200: Relançar para preservar detalhes da pilha](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Uma exceção é relançada e a exceção é explicitamente especificada na instrução Throw. Se uma exceção for relançada especificando a exceção na instrução throw, a lista de chamadas de método entre o método original que gerou a exceção e o método atual será perdida.|
|[CA2201: Não acionar tipos de exceção reservados](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|Isso torna o erro original difícil de detectar e depurar.|
|[CA2202: Não descartar objetos várias vezes](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Uma implementação do método contém caminhos de código que poderiam causar várias chamadas para System.IDisposable.Dispose ou para um equivalente a Dispose (como um método Close() em alguns tipos) no mesmo objeto.|
|[CA2204: Literais devem ser escritos corretamente](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|Uma cadeia de caracteres literal em um corpo de método contém uma ou mais palavras não reconhecidas pela biblioteca do verificador ortográfico da Microsoft.|
|[CA2205: Usar equivalentes gerenciados da API do Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Um método de invocação de plataforma é definido e um método com a funcionalidade equivalente existe na biblioteca de classes .NET Framework.|
|[CA2207: Inicializar campos estáticos de tipo de valor em linha](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Um tipo de valor declara um construtor estático explícito. Para corrigir uma violação dessa regra, inicialize todos os dados estáticos quando declarados e remova o construtor estático.|
|[CA2208: Criar instância de exceções de argumento corretamente](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|For feita uma chamada para o construtor padrão (sem parâmetros) de um tipo de exceção que seja ou derive de ArgumentException, ou um argumento de cadeia de caracteres incorreto é passado para um construtor com parâmetros de um tipo de exceção que seja ou derive de ArgumentException.|
|[CA2211: Campos não constantes não devem ser visíveis](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Os campos estáticos que não são constantes nem somente leitura não são thread-safe. O acesso a esse campo deve ser cuidadosamente controlado e requer técnicas de programação avançadas para sincronizar o acesso ao objeto de classe.|
|[CA2212: Não marcar componentes atendidos com WebMethod](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Um método em um tipo que herda de System. EnterpriseServices. ServicedComponent é marcado com System. Web. Services. WebMethodAttribute. Como WebMethodAttribute e um método ServicedComponent têm comportamento e requisitos conflitantes para o contexto e o fluxo de transações, o comportamento do método estará incorreto em alguns cenários.|
|[CA2213: Campos descartáveis devem ser descartados](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Um tipo que implementa System.IDisposable declara campos que são de tipos que também implementam IDisposable. O método Dispose do campo não é chamado pelo método Dispose do tipo declarante.|
|[CA2214: Não chamar métodos substituíveis em construtores](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|Quando um construtor chama um método virtual, é possível que o construtor da instância que invoca o método não tenha sido executado.|
|[CA2215: Métodos Dispose devem chamar o descarte da classe base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)|Se for herdado de um tipo descartável, um tipo deverá chamar o método Dispose do tipo de base em seu próprio método Dispose.|
|[CA2216: Tipos descartáveis devem declarar o finalizador](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Um tipo que implementa System. IDisposable e tem campos que sugerem o uso de recursos não gerenciados, não implementa um finalizador, conforme descrito por Object. Finalize.|
|[CA2217: Não marcar enumerações com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Uma enumeração visível externamente é marcada com FlagsAttribute e tem um ou mais valores que não são potências de duas ou uma combinação de outros valores definidos na enumeração.|
|[CA2218: Substituir GetHashCode ao substituir Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)|GetHashCode retorna um valor, com base na instância atual, adequado para algoritmos de hash e estruturas de dados como uma tabela de hash. Dois objetos que tenham o mesmo tipo e sejam iguais devem retornar o mesmo código hash.|
|[CA2219: Não acionar exceções em cláusulas de exceção](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Quando uma exceção é acionada em uma cláusula finally ou fault, a nova exceção oculta a exceção ativa. Quando uma exceção é acionada em uma cláusula de filtro, o tempo de execução captura silenciosamente a exceção. Isso torna o erro original difícil de detectar e depurar.|
|[CA2220: Os finalizadores devem chamar o finalizador de classe base](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|A finalização deve ser propagada em toda a hierarquia de herança. Para garantir isso, os tipos devem chamar o método Finalize de classe base em seu próprio método Finalize.|
|[CA2221: Os finalizadores devem ser protegidos](../code-quality/ca2221-finalizers-should-be-protected.md)|Os finalizadores deve usar o modificador de acesso da família.|
|[CA2222: Não diminuir a visibilidade dos membros herdados](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Você não deve alterar o modificador de acesso para membros herdados. A alteração de um membro herdado para particular não impede que os chamadores acessem a implementação da classe base do método.|
|[CA2223: Os membros devem ser diferentes em algo além de um tipo de retorno](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Embora o Common Language Runtime permita o uso de tipos de retorno na diferenciação de membros outrora idênticos, este recurso não está na CLS nem é um recurso comum das linguagens de programação do .NET.|
|[CA2224: Substituir equals ao sobrecarregar operador equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Um tipo público implementa o operador de igualdade, mas não substitui Object. Equals.|
|[CA2225: Sobrecargas de operador têm alternativas nomeadas](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|Uma sobrecarga de operador foi detectada, e o método alternativo nomeado esperado não foi encontrado. O membro alternativo nomeado fornece acesso à mesma funcionalidade que o operador e é fornecido para desenvolvedores que programam em idiomas que não dão suporte a operadores sobrecarregados.|
|[CA2226: Operadores devem ter sobrecargas simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Um tipo implementa o operador de igualdade ou desigualdade e não implementa o operador oposto.|
|[CA2227: Propriedades de coleção devem ser somente leitura](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Uma propriedade collection gravável permite que um usuário substitua a coleção por uma coleção diferente. Uma propriedade somente leitura evita que a coleção seja substituída, mas ainda permite que membros individuais sejam definidos.|
|[CA2228: Não fornecer formatos de recurso não lançados](../code-quality/ca2228-do-not-ship-unreleased-resource-formats.md)|Os arquivos de recursos criados com versões de pré-lançamento do .NET Framework podem não ser utilizáveis por versões com suporte do .NET Framework.|
|[CA2229: Implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)|Para corrigir uma violação dessa regra, implemente o construtor de serialização. Para uma classe lacrada, torne o construtor particular; do contrário, deixe-o protegido.|
|[CA2230: Usar parâmetros para argumentos variáveis](../code-quality/ca2230-use-params-for-variable-arguments.md)|Um tipo público ou protegido contém um método público ou protegido que usa a convenção de chamada VarArgs, em vez da palavra-chave params.|
|[CA2231: Sobrecarregar operador equals ao substituir ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Um tipo de valor substitui Object.Equals, mas não implementa o operador de igualdade.|
|[CA2232: Marcar pontos de entrada do Windows Forms com STAThread](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|STAThreadAttribute indica que o modelo de threading COM para o aplicativo é um single-threaded apartment. Esse atributo deve estar presente no ponto de entrada de qualquer aplicativo que use o Windows Forms; se ele for omitido, os componentes do Windows poderão não funcionar corretamente.|
|[CA2233: As operações não devem estourar](../code-quality/ca2233-operations-should-not-overflow.md)|As operações aritméticas não devem ser executadas sem validar primeiro os operandos, para garantir que o resultado da operação não esteja fora do intervalo de valores possíveis para os tipos de dados envolvidos.|
|[CA2234: Passar objetos System.Uri em vez de cadeias de caracteres](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Foi feita uma chamada para um método com um parâmetro de cadeia de caracteres cujo nome contém "uri", "URI", "urn", "URN", "url" ou "URL".  O tipo declarante do método contém uma sobrecarga do método correspondente que possui um parâmetro System.Uri.|
|[CA2235: Marcar todos os campos não serializáveis](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Um campo de instância de um tipo que não seja serializável é declarado em um tipo que é serializável.|
|[CA2236: Chamar métodos da classe base em tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Para corrigir uma violação dessa regra, chame o método GetObjectData de tipo base ou o construtor de serialização do método de tipo derivado correspondente ou do construtor.|
|[CA2237: Marcar tipos ISerializable com SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Para ser reconhecido pelo Common Language Runtime como serializável, os tipos devem ser marcados com o atributo SerializableAttribute, mesmo que o tipo use uma rotina de serialização personalizada por meio da implementação da interface ISerializable.|
|[CA2238: Implementar métodos de serialização corretamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Um método que trata um evento de serialização não tem a assinatura, o tipo de retorno ou a visibilidade corretos.|
|[CA2239: Fornecer métodos de desserialização para campos opcionais](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Um tipo tem um campo que é marcado com o atributo System. Runtime. Serialization. OptionalFieldAttribute e o tipo não fornece métodos de manipulação de eventos de serialização.|
|[CA2240: Implementar ISerializable corretamente](../code-quality/ca2240-implement-iserializable-correctly.md)|Para corrigir uma violação dessa regra, torne o método GetObjectData visível e substituível e verifique se todos os campos de instância estão incluídos no processo de serialização ou explicitamente marcados com o atributo nonserializadoattribute.|
|[CA2241: Fornecer argumentos corretos para métodos de formatação](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|O argumento de formato passado para System. String. Format não contém um item de formato que corresponde a cada argumento de objeto ou vice-versa.|
|[CA2242: Testar para NaN corretamente](../code-quality/ca2242-test-for-nan-correctly.md)|Essa expressão testa um valor em Single.Nan ou Double.Nan. Use Single.IsNan (único) ou Double.IsNan (duplo) para testar o valor.|
|[CA2243: Literais de cadeias de caracteres de atributo devem ser analisados corretamente](../code-quality/ca2243-attribute-string-literals-should-parse-correctly.md)|O parâmetro literal da cadeia de caracteres de um atributo não é analisado corretamente para uma URL, um GUID ou uma versão.|
