---
title: Conjunto de regras recomendadas nativo
ms.date: 11/04/2016
description: Saiba mais sobre o conjunto de regras de regras recomendadas nativas do Visual Studio. Veja descrições de regras de segurança, robustez e outros problemas críticos no código nativo.
ms.custom: SEO-VS-2020
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c0515a08d987d8892dd5f252d97ece8d138eb0b
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437025"
---
# <a name="native-recommended-rules-rule-set"></a>Conjunto de regras recomendadas nativo

As regras nativas recomendadas se concentram nos problemas mais críticos e comuns no código nativo, incluindo possíveis falhas de segurança e aplicativos. Esse conjunto de regras inclui todas as regras no conjunto de regras de [regras mínimas nativas](native-minimum-rules-rule-set.md) .

Inclua esse conjunto de regras em qualquer conjunto personalizado de regras que você criar para projetos nativos.

|Regra|Descrição|
|----------|-----------------|
|[C6001](/cpp/code-quality/c6001)|Uso de memória não inicializada|
|[C6011](/cpp/code-quality/c6011)|Desreferenciando ponteiro nulo|
|[C6029](/cpp/code-quality/c6029)|Uso de valores não marcados|
|[C6031](/cpp/code-quality/c6031)|Valor de retorno ignorado|
|[C6053](/cpp/code-quality/c6053)|Terminação em zero da chamada|
|[C6054](/cpp/code-quality/c6054)|Encerramento zero ausente|
|[C6059](/cpp/code-quality/c6059)|Concatenação defeituosa|
|[C6063](/cpp/code-quality/c6063)|Argumento da cadeia de caracteres ausente para formatar função|
|[C6064](/cpp/code-quality/c6064)|Argumento inteiro ausente para formatar função|
|[C6066](/cpp/code-quality/c6066)|Argumento de ponteiro ausente para formatar função|
|[C6067](/cpp/code-quality/c6067)|Argumento de ponteiro de cadeia de caracteres ausente para formatar função|
|[C6101](/cpp/code-quality/c6101)|Retornando a memória não inicializada|
|[C6200](/cpp/code-quality/c6200)|O índice excede o máximo do buffer|
|[C6201](/cpp/code-quality/c6201)|O índice excede o máximo do buffer da pilha|
|[C6214](/cpp/code-quality/c6214)|Conversão de HRESULT para BOOL inválida|
|[C6215](/cpp/code-quality/c6215)|Conversão de BOOL para HRESULT inválida|
|[C6216](/cpp/code-quality/c6216)|Conversão de Compiler-Inserted inválida BOOL para HRESULT|
|[C6217](/cpp/code-quality/c6217)|Teste de HRESULT inválido com não|
|[C6220](/cpp/code-quality/c6220)|Comparação de HRESULT com-1 inválida|
|[C6226](/cpp/code-quality/c6226)|Atribuição de HRESULT inválida para-1|
|[C6230](/cpp/code-quality/c6230)|Uso inválido de HRESULT como booliano|
|[C6235](/cpp/code-quality/c6235)|Constante diferente de zero com Logical-Or|
|[C6236](/cpp/code-quality/c6236)|Logical-Or com constante diferente de zero|
|[C6237](/cpp/code-quality/c6237)|Zero com Logical-And perde efeitos colaterais|
|[C6242](/cpp/code-quality/c6242)|Desenrolamento local forçado|
|[C6248](/cpp/code-quality/c6248)|Criando DACL nula|
|[C6250](/cpp/code-quality/c6250)|Descritores de endereço não lançados|
|[C6255](/cpp/code-quality/c6255)|Uso desprotegido de alloca|
|[C6258](/cpp/code-quality/c6258)|Usando encerrar thread|
|[C6259](/cpp/code-quality/c6259)|Código inativo em Bitwise-Or comutador limitado|
|[C6260](/cpp/code-quality/c6260)|Uso de aritmética de byte|
|[C6262](/cpp/code-quality/c6262)|Uso excessivo de pilha|
|[C6263](/cpp/code-quality/c6263)|Usando alloca em loop|
|[C6268](/cpp/code-quality/c6268)|Parênteses ausentes na conversão|
|[C6269](/cpp/code-quality/c6269)|Desreferência de ponteiro ignorada|
|[C6270](/cpp/code-quality/c6270)|Falta argumento float para formatar a função|
|[C6271](/cpp/code-quality/c6271)|Argumento extra para formatar função|
|[C6272](/cpp/code-quality/c6272)|Argumento diferente de float para formatar a função|
|[C6273](/cpp/code-quality/c6273)|Argumento não inteiro para formatar a função|
|[C6274](/cpp/code-quality/c6274)|Argumento diferente de caractere para formatar a função|
|[C6276](/cpp/code-quality/c6276)|Conversão de cadeia de caracteres inválida|
|[C6277](/cpp/code-quality/c6277)|Chamada CreateProcess inválida|
|[C6278](/cpp/code-quality/c6278)|Incompatibilidade de Array-New Scalar-Delete|
|[C6279](/cpp/code-quality/c6279)|Incompatibilidade de Scalar-New Array-Delete|
|[C6280](/cpp/code-quality/c6280)|Memória incompatível Allocation-Deallocation|
|[C6281](/cpp/code-quality/c6281)|Precedência de relação bit-nte|
|[C6282](/cpp/code-quality/c6282)|A atribuição substitui o teste|
|[C6283](/cpp/code-quality/c6283)|Array-New primitivo Scalar-Delete incompatível|
|[C6284](/cpp/code-quality/c6284)|Argumento de objeto inválido para formatar a função|
|[C6285](/cpp/code-quality/c6285)|Logical-Or de constantes|
|[C6286](/cpp/code-quality/c6286)|Diferente de zero Logical-Or perder efeitos colaterais|
|[C6287](/cpp/code-quality/c6287)|Teste redundante|
|[C6288](/cpp/code-quality/c6288)|A inclusão mútua sobre Logical-And é false|
|[C6289](/cpp/code-quality/c6289)|A exclusão mútua sobre Logical-Or é verdadeira|
|[C6290](/cpp/code-quality/c6290)|Precedência de NOT lógico AND bit a bit|
|[C6291](/cpp/code-quality/c6291)|Precedência de NOT lógico OR bit a bit|
|[C6292](/cpp/code-quality/c6292)|Contagens de loops acima do máximo|
|[C6293](/cpp/code-quality/c6293)|Contagens de loops abaixo do mínimo|
|[C6294](/cpp/code-quality/c6294)|Corpo do loop nunca executado|
|[C6295](/cpp/code-quality/c6295)|Loop infinito|
|[C6296](/cpp/code-quality/c6296)|Loop executado apenas uma vez|
|[C6297](/cpp/code-quality/c6297)|Resultado da conversão de deslocamento para tamanho maior|
|[C6299](/cpp/code-quality/c6299)|Comparação de campo de bits para booliano|
|[C6302](/cpp/code-quality/c6302)|Argumento da cadeia de caracteres inválido para formatar a função|
|[C6303](/cpp/code-quality/c6303)|Argumento da cadeia de caracteres larga inválido para formatar a função|
|[C6305](/cpp/code-quality/c6305)|Uso incompatível de tamanho e contagem|
|[C6306](/cpp/code-quality/c6306)|Chamada de função de argumento variável incorreta|
|[C6308](/cpp/code-quality/c6308)|Vazamento de realocação|
|[C6310](/cpp/code-quality/c6310)|Constante de filtro de exceção ilegal|
|[C6312](/cpp/code-quality/c6312)|Loop de execução de continuação de exceção|
|[C6314](/cpp/code-quality/c6314)|Precedência de Bitwise-Or|
|[C6317](/cpp/code-quality/c6317)|Não é complemento|
|[C6318](/cpp/code-quality/c6318)|Exceção de continuação da pesquisa|
|[C6319](/cpp/code-quality/c6319)|Ignorado por vírgula|
|[C6324](/cpp/code-quality/c6324)|Cópia de cadeia de caracteres em vez de comparação de cadeia|
|[C6328](/cpp/code-quality/c6328)|Incompatibilidade potencial de tipo de argumento|
|[C6331](/cpp/code-quality/c6331)|VirtualFree Sinalizadores inválidos|
|[C6332](/cpp/code-quality/c6332)|VirtualFree parâmetro inválido|
|[C6333](/cpp/code-quality/c6333)|VirtualFree tamanho inválido|
|[C6335](/cpp/code-quality/c6335)|Vazamento de identificador de processo|
|[C6381](/cpp/code-quality/c6381)|Informações de desligamento ausentes|
|[C6383](/cpp/code-quality/c6383)|Saturação de buffer de Byte-Count Element-Count|
|[C6384](/cpp/code-quality/c6384)|Divisão do tamanho do ponteiro|
|[C6385](/cpp/code-quality/c6385)|Saturação de leitura|
|[C6386](/cpp/code-quality/c6386)|Saturação de gravação|
|[C6387](/cpp/code-quality/c6387)|Valor de parâmetro inválido|
|[C6388](/cpp/code-quality/c6388)|Valor de parâmetro inválido|
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
|[C6995](/cpp/code-quality/c6995)|Falha ao salvar o arquivo de log XML|
|[C26100](/cpp/code-quality/c26100)|Condição de corrida|
|[C26101](/cpp/code-quality/c26101)|Falha ao usar a operação Interlocked corretamente|
|[C26110](/cpp/code-quality/c26110)|Chamador falhando ao manter bloqueio|
|[C26111](/cpp/code-quality/c26111)|Chamador falhando ao liberar bloqueio|
|[C26112](/cpp/code-quality/c26112)|O chamador não pode conter nenhum bloqueio|
|[C26115](/cpp/code-quality/c26115)|Falha ao liberar bloqueio|
|[C26116](/cpp/code-quality/c26116)|Falha ao adquirir ou manter bloqueio|
|[C26117](/cpp/code-quality/c26117)|Liberando bloqueio não mantido|
|[C26140](/cpp/code-quality/c26140)|Erro de anotação de SAL de simultaneidade|
|[C26441](/cpp/code-quality/C26441)|NO_UNNAMED_GUARDS|
|[C26444](/cpp/code-quality/c26444)|NO_UNNAMED_RAII_OBJECTS|
|[C26498](/cpp/code-quality/C26498)|USE_CONSTEXPR_FOR_FUNCTIONCALL|
|[C28020](/cpp/code-quality/c28020)|A expressão não é verdadeira nesta chamada|
|[C28021](/cpp/code-quality/c28021)|O parâmetro que está sendo anotado deve ser um ponteiro|
|[C28022](/cpp/code-quality/c28022)|As classes de função nessa função não correspondem às classes de função no typedef usado para defini-la.|
|[C28023](/cpp/code-quality/c28023)|A função que está sendo atribuída ou passada deve ter uma \_ \_ \_ anotação de classe de função para pelo menos uma das classes|
|[C28024](/cpp/code-quality/c28024)|O ponteiro de função que está sendo atribuído é anotado com a classe de função, que não está contida na lista de classe (s) de função.|
|[C28039](/cpp/code-quality/c28039)|O tipo de parâmetro real deve corresponder exatamente ao tipo|
|[C28112](/cpp/code-quality/c28112)|Uma variável que é acessada por meio de uma função Interlocked sempre deve ser acessada por meio de uma função Interlocked.|
|[C28113](/cpp/code-quality/c28113)|Acessando uma variável local por meio de uma função Interlocked|
|[C28125](/cpp/code-quality/c28125)|A função deve ser chamada de dentro de um bloco try/Except|
|[C28137](/cpp/code-quality/c28137)|O argumento da variável deve ser uma constante (literal)|
|[C28138](/cpp/code-quality/c28138)|O argumento de constante deve ser variável|
|[C28159](/cpp/code-quality/c28159)|Considere usar outra função em vez disso.|
|[C28160](/cpp/code-quality/c28160)|Anotação de erro|
|[C28163](/cpp/code-quality/c28163)|A função nunca deve ser chamada de dentro de um bloco try/Except|
|[C28164](/cpp/code-quality/c28164)|O argumento está sendo passado para uma função que espera um ponteiro para um objeto (não um ponteiro para um ponteiro)|
|[C28182](/cpp/code-quality/c28182)|Desreferenciando ponteiro nulo. O ponteiro contém o mesmo valor NULO que outro ponteiro tinha.|
|[C28183](/cpp/code-quality/c28183)|O argumento pode ser um valor e é uma cópia do valor encontrado no ponteiro|
|[C28193](/cpp/code-quality/c28193)|A variável contém um valor que deve ser examinado|
|[C28196](/cpp/code-quality/c28196)|O requisito não é atendido. (A expressão não é avaliada como true.)|
|[C28202](/cpp/code-quality/c28202)|Referência inválida para membro não estático|
|[C28203](/cpp/code-quality/c28203)|Referência ambígua ao membro de classe.|
|[C28205](/cpp/code-quality/c28205)|\_Êxito \_ ou \_ em \_ caso de falha \_ usada em um contexto ilegal|
|[C28206](/cpp/code-quality/c28206)|O operando da esquerda aponta para um struct, use '->'|
|[C28207](/cpp/code-quality/c28207)|O operando da esquerda é um struct, use '.'|
|[C28209](/cpp/code-quality/c28209)|A declaração de Symbol tem uma declaração conflitante|
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
|[C28244](/cpp/code-quality/c28244)|A anotação for function tem um parâmetro/anotação externa não analisável|
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
|[C28306](/cpp/code-quality/c28306)|A anotação no parâmetro é obsoleta|
|[C28307](/cpp/code-quality/c28307)|A anotação no parâmetro é obsoleta|
|[C28350](/cpp/code-quality/c28350)|A anotação descreve uma situação que não é aplicável condicionalmente.|
|[C28351](/cpp/code-quality/c28351)|A anotação descreve onde um valor dinâmico (uma variável) não pode ser usado na condição.|