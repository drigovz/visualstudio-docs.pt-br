---
title: Conjunto de regras mínimas nativo
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 2d898bc4-fba5-472e-8f09-b0c6b511c5a3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5646986381907d6ba524b27ae28985e579d6e379
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89600034"
---
# <a name="native-minimum-rules-rule-set"></a>Conjunto de regras mínimas nativo

As regras mínimas nativas da Microsoft concentram-se nos problemas mais críticos no código nativo, incluindo falhas de segurança e falhas do aplicativo.

Inclua esse conjunto de regras em qualquer conjunto personalizado de regras que você criar para projetos nativos.

|Regra|Descrição|
|----------|-----------------|
|[C6001](/cpp/code-quality/c6001)|Uso de memória não inicializada|
|[C6011](/cpp/code-quality/c6011)|Desreferenciando ponteiro nulo|
|[C6029](/cpp/code-quality/c6029)|Uso de valores não marcados|
|[C6053](/cpp/code-quality/c6053)|Terminação em zero da chamada|
|[C6059](/cpp/code-quality/c6059)|Concatenação defeituosa|
|[C6063](/cpp/code-quality/c6063)|Argumento da cadeia de caracteres ausente para formatar função|
|[C6064](/cpp/code-quality/c6064)|Argumento inteiro ausente para formatar função|
|[C6066](/cpp/code-quality/c6066)|Argumento de ponteiro ausente para formatar função|
|[C6067](/cpp/code-quality/c6067)|Argumento de ponteiro de cadeia de caracteres ausente para formatar função|
|[C6101](/cpp/code-quality/c6101)|Retornando a memória não inicializada|
|[C6200](/cpp/code-quality/c6200)|O índice excede o máximo do buffer|
|[C6201](/cpp/code-quality/c6201)|O índice excede o máximo do buffer da pilha|
|[C6270](/cpp/code-quality/c6270)|Falta argumento float para formatar a função|
|[C6271](/cpp/code-quality/c6271)|Argumento extra para formatar função|
|[C6272](/cpp/code-quality/c6272)|Argumento diferente de float para formatar a função|
|[C6273](/cpp/code-quality/c6273)|Argumento não inteiro para formatar a função|
|[C6274](/cpp/code-quality/c6274)|Argumento diferente de caractere para formatar a função|
|[C6276](/cpp/code-quality/c6276)|Conversão de cadeia de caracteres inválida|
|[C6277](/cpp/code-quality/c6277)|Chamada CreateProcess inválida|
|[C6284](/cpp/code-quality/c6284)|Argumento de objeto inválido para formatar a função|
|[C6290](/cpp/code-quality/c6290)|Precedência de NOT lógico AND bit a bit|
|[C6291](/cpp/code-quality/c6291)|Precedência de NOT lógico OR bit a bit|
|[C6302](/cpp/code-quality/c6302)|Argumento da cadeia de caracteres inválido para formatar a função|
|[C6303](/cpp/code-quality/c6303)|Argumento da cadeia de caracteres larga inválido para formatar a função|
|[C6305](/cpp/code-quality/c6305)|Uso incompatível de tamanho e contagem|
|[C6306](/cpp/code-quality/c6306)|Chamada de função de argumento variável incorreta|
|[C6328](/cpp/code-quality/c6328)|Incompatibilidade potencial de tipo de argumento|
|[C6385](/cpp/code-quality/c6385)|Saturação de leitura|
|[C6386](/cpp/code-quality/c6386)|Saturação de gravação|
|[C6387](/cpp/code-quality/c6387)|Valor de parâmetro inválido|
|[C6500](/cpp/code-quality/c6500)|Propriedade de atributo inválida|
|[C6501](/cpp/code-quality/c6501)|Conflito de valores de propriedades do atributo|
|[C6503](/cpp/code-quality/c6503)|As referências não podem ser nulas|
|[C6504](/cpp/code-quality/c6504)|Nulo em não ponteiro|
|[C6505](/cpp/code-quality/c6505)|MustCheck em nulo|
|[C6506](/cpp/code-quality/c6506)|Tamanho do buffer em não ponteiro ou matriz|
|[C6508](/cpp/code-quality/c6508)|Acesso para gravação na constante|
|[C6509](/cpp/code-quality/c6509)|Retorno usado em pré condição|
|[C6510](/cpp/code-quality/c6510)|Terminação nula em não ponteiro|
|[C6511](/cpp/code-quality/c6511)|MustCheck deve ser Sim ou Não|
|[C6513](/cpp/code-quality/c6513)|Tamanho do elemento sem tamanho do buffer|
|[C6514](/cpp/code-quality/c6514)|O tamanho do buffer excede o tamanho da matriz|
|[C6515](/cpp/code-quality/c6515)|Tamanho do buffer em não ponteiro|
|[C6516](/cpp/code-quality/c6516)|Nenhuma propriedade no atributo|
|[C6517](/cpp/code-quality/c6517)|Tamanho válido em buffer não legível|
|[C6518](/cpp/code-quality/c6518)|Tamanho gravável em buffer não gravável|
|[C6522](/cpp/code-quality/c6522)|Tipo de cadeia de caracteres de tamanho inválido|
|[C6525](/cpp/code-quality/c6525)|Local inatingível da cadeia de caracteres inválido|
|[C6527](/cpp/code-quality/c6527)|Anotação inválida: A propriedade 'NeedsRelease' não pode ser utilizada em valores de tipo void|
|[C6530](/cpp/code-quality/c6530)|Estilo de cadeia de caracteres de formato não reconhecido|
|[C6540](/cpp/code-quality/c6540)|O uso de anotações de atributo nesta função irá invalidar todas as anotações __declspec existentes na função|
|[C6551](/cpp/code-quality/c6551)|Especificação de tamanho inválido: expressão não analisável|
|[C6552](/cpp/code-quality/c6552)|Deref= ou Notref= inválidos: expressão não analisável|
|[C6701](/cpp/code-quality/c6701)|O valor não é um valor Sim/Não/Talvez válido|
|[C6702](/cpp/code-quality/c6702)|O valor não é um valor de cadeia de caracteres|
|[C6703](/cpp/code-quality/c6703)|O valor não é um número|
|[C6704](/cpp/code-quality/c6704)|Erro de Expressão de Anotação inesperada|
|[C6705](/cpp/code-quality/c6705)|Número esperado de argumentos para anotação não corresponde ao número de argumentos real para anotação|
|[C6706](/cpp/code-quality/c6706)|Erro inesperado de anotação para anotação|
|[C26450](/cpp/code-quality/C26450)|RESULT_OF_ARITHMETIC_OPERATION_PROVABLY_LOSSY|
|[C26451](/cpp/code-quality/C26451)|RESULT_OF_ARITHMETIC_OPERATION_CAST_TO_LARGER_SIZE|
|[C26452](/cpp/code-quality/C26452)|SHIFT_COUNT_NEGATIVE_OR_TOO_BIG|
|[C26453](/cpp/code-quality/C26453)|LEFTSHIFT_NEGATIVE_SIGNED_NUMBER|
|[C26454](/cpp/code-quality/C26454)|RESULT_OF_ARITHMETIC_OPERATION_NEGATIVE_UNSIGNED|
|[C26495](/cpp/code-quality/C26495)|MEMBER_UNINIT|
|[C28021](/cpp/code-quality/c28021)|O parâmetro que está sendo anotado deve ser um ponteiro|
|[C28182](/cpp/code-quality/c28182)|Desreferenciando ponteiro nulo. O ponteiro contém o mesmo valor NULO que outro ponteiro tinha.|
|[C28202](/cpp/code-quality/c28202)|Referência inválida para membro não estático|
|[C28203](/cpp/code-quality/c28203)|Referência ambígua ao membro de classe.|
|[C28205](/cpp/code-quality/c28205)|\_Êxito \_ ou \_ em \_ caso de falha \_ usada em um contexto ilegal|
|[C28206](/cpp/code-quality/c28206)|O operando da esquerda aponta para um struct, use '->'|
|[C28207](/cpp/code-quality/c28207)|O operando da esquerda é um struct, use '.'|
|[C28210](/cpp/code-quality/c28210)|Anotações para o contexto __on_failure não devem estar no pré-contexto explícito|
|[C28211](/cpp/code-quality/c28211)|Nome esperado do contexto estático para SAL_context|
|[C28212](/cpp/code-quality/c28212)|Expressão de ponteiro esperada para anotação|
|[C28213](/cpp/code-quality/c28213)|A \_ anotação usar as \_ anotações de decl \_ \_ deve ser usada para fazer referência, sem modificação, de uma declaração anterior.|
|[C28214](/cpp/code-quality/c28214)|Os nomes do parâmetro de atributo devem ser p1...p9|
|[C28215](/cpp/code-quality/c28215)|O typefix não pode ser aplicado a um parâmetro que já tem um typefix|
|[C28216](/cpp/code-quality/c28216)|A anotação checkReturn se aplica apenas a pós-condições para o parâmetro da função específica.|
|[C28217](/cpp/code-quality/c28217)|Para função, o número de parâmetros para anotação não corresponde ao encontrado no arquivo|
|[C28218](/cpp/code-quality/c28218)|Para o parâmetro de função, o parâmetro da anotação não corresponde ao encontrado no arquivo|
|[C28219](/cpp/code-quality/c28219)|Membro de enumeração esperada para anotação do parâmetro na anotação|
|[C28220](/cpp/code-quality/c28220)|Expressão inteira esperada para anotação do parâmetro na anotação|
|[C28221](/cpp/code-quality/c28221)|Expressão de sequência de caracteres esperada para o parâmetro na anotação|
|[C28222](/cpp/code-quality/c28222)|__yes, \__no ou \__maybe esperados para anotação|
|[C28223](/cpp/code-quality/c28223)|O token/identificador esperado para anotação não encontrado, parâmetro|
|[C28224](/cpp/code-quality/c28224)|Anotação requer parâmetros|
|[C28225](/cpp/code-quality/c28225)|O número correto de parâmetros necessários na anotação não foi encontrado|
|[C28226](/cpp/code-quality/c28226)|Anotação não pode ser também um PrimOp (na declaração atual)|
|[C28227](/cpp/code-quality/c28227)|A anotação não pode ser também um PrimOp (veja a declaração anterior)|
|[C28228](/cpp/code-quality/c28228)|Parâmetro de anotação: não é possível usar tipo nas anotações|
|[C28229](/cpp/code-quality/c28229)|A anotação não tem suporte a parâmetros|
|[C28230](/cpp/code-quality/c28230)|O tipo de parâmetro não tem membro.|
|[C28231](/cpp/code-quality/c28231)|A anotação só é válida na matriz|
|[C28232](/cpp/code-quality/c28232)|pre, post ou deref não aplicados a qualquer anotação|
|[C28233](/cpp/code-quality/c28233)|pre, post ou deref aplicados a um bloco|
|[C28234](/cpp/code-quality/c28234)|__na expressão não se aplica à função atual|
|[C28235](/cpp/code-quality/c28235)|A função não pode ser autônoma como uma anotação|
|[C28236](/cpp/code-quality/c28236)|A anotação não pode ser usada em uma expressão|
|[C28237](/cpp/code-quality/c28237)|A anotação no parâmetro não é mais suportada|
|[C28238](/cpp/code-quality/c28238)|A anotação no parâmetro tem mais de um do valor, stringValue e longValue. Utilize paramn=xxx|
|[C28239](/cpp/code-quality/c28239)|A anotação no parâmetro tem os dois valores, stringValue e longValue; e paramn=xxx. Utilize apenas paramn=xxx|
|[C28240](/cpp/code-quality/c28240)|A anotação no parâmetro tem param2, mas não tem param1|
|[C28241](/cpp/code-quality/c28241)|A anotação para função no parâmetro não é reconhecida|
|[C28243](/cpp/code-quality/c28243)|A anotação para função no parâmetro requer mais desreferências do que o tipo real anotado permite|
|[C28245](/cpp/code-quality/c28245)|A anotação para função anota 'este' em uma função não membro|
|[C28246](/cpp/code-quality/c28246)|A anotação do parâmetro para função não corresponde ao tipo do parâmetro|
|[C28250](/cpp/code-quality/c28250)|Anotação inconsistente para função: a instância anterior tem um erro.|
|[C28251](/cpp/code-quality/c28251)|Anotação inconsistente para função: esta instância tem um erro.|
|[C28252](/cpp/code-quality/c28252)|Anotação inconsistente para função: o parâmetro tem outras anotações nesta instância.|
|[C28253](/cpp/code-quality/c28253)|Anotação inconsistente para função: o parâmetro tem outras anotações nesta instância.|
|[C28254](/cpp/code-quality/c28254)|dynamic_cast<>() não tem suporte nas anotações|
|[C28262](/cpp/code-quality/c28262)|Foi encontrado um erro de sintaxe na anotação na função, para anotação|
|[C28263](/cpp/code-quality/c28263)|Foi encontrado um erro de sintaxe em uma anotação condicional na anotação intrínseca|
|[C28267](/cpp/code-quality/c28267)|Foi encontrado um erro de sintaxe nas anotações da função.|
|[C28272](/cpp/code-quality/c28272)|A anotação para função, parâmetro quando examinar for inconsistente com a declaração da função|
|[C28273](/cpp/code-quality/c28273)|Para função, os indícios são inconsistentes com a declaração da função|
|[C28275](/cpp/code-quality/c28275)|O parâmetro para \_ o \_ valor da macro \_ é nulo|
|[C28279](/cpp/code-quality/c28279)|Para símbolo, um 'início' foi encontrado sem um 'fim' correspondente|
|[C28280](/cpp/code-quality/c28280)|Para símbolo, um 'fim' foi encontrado sem um 'início' correspondente|
|[C28282](/cpp/code-quality/c28282)|Cadeias de caracteres de formato devem estar em pré-condições|
|[C28285](/cpp/code-quality/c28285)|Para função, erro de sintaxe no parâmetro|
|[C28286](/cpp/code-quality/c28286)|Para função, erro de sintaxe perto do fim|
|[C28287](/cpp/code-quality/c28287)|Para função, Erro de sintaxe na anotação \_At\_() (nome de parâmetro não reconhecido)|
|[C28288](/cpp/code-quality/c28288)|Para função, Erro de sintaxe na anotação \_At\_() (nome de parâmetro inválido)|
|[C28289](/cpp/code-quality/c28289)|Para função: ReadableTo ou WritableTo não tinha uma especificação de limite como parâmetro|
|[C28290](/cpp/code-quality/c28290)|a anotação para função contém mais Externos que o número real de parâmetros|
|[C28291](/cpp/code-quality/c28291)|pós null/notnull em deref nível 0 não tem sentido para a função.|
|[C28300](/cpp/code-quality/c28300)|Operandos da expressão de tipos incompatíveis para o operador|
|[C28301](/cpp/code-quality/c28301)|Não há anotações para a primeira declaração da função.|
|[C28302](/cpp/code-quality/c28302)|Foi encontrado um operador extra \_Deref\_ na anotação.|
|[C28303](/cpp/code-quality/c28303)|Foi encontrado um operador ambíguo \_Deref\_ na anotação.|
|[C28304](/cpp/code-quality/c28304)|Foi encontrado um operador \_Notref\_ posicionado inadequadamente aplicado ao token.|
|[C28305](/cpp/code-quality/c28305)|Foi encontrado um erro durante a análise de um token.|
|[C28350](/cpp/code-quality/c28350)|A anotação descreve uma situação que não é aplicável condicionalmente.|
|[C28351](/cpp/code-quality/c28351)|A anotação descreve onde um valor dinâmico (uma variável) não pode ser usado na condição.|