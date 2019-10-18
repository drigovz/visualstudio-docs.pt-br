---
title: Conjunto de regras recomendadas misto
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1940680af30928b46dbb73616569d0db318dac18
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72535732"
---
# <a name="mixed-recommended-rules-rule-set"></a>Conjunto de regras recomendadas misto

As regras recomendadas mistas da Microsoft concentram-se nos problemas mais C++ comuns e críticos em seus projetos que dão suporte ao Common Language Runtime, incluindo possíveis falhas de segurança, falhas do aplicativo e outros erros importantes de lógica e design. Esse conjunto de regras inclui todas as regras no conjunto de regras de [regras de mínimos mistos](mixed-minimum-rules-rule-set.md) .

Inclua esse conjunto de regras em qualquer conjunto personalizado de regras que você C++ criar para seus projetos que dão suporte ao Common Language Runtime.

|Regra|Descrição|
|----------|-----------------|
|[C6001](../code-quality/c6001.md)|Uso de memória não inicializada|
|[C6011](../code-quality/c6011.md)|Desreferenciando ponteiro nulo|
|[C6029](../code-quality/c6029.md)|Uso de valores não marcados|
|[C6031](../code-quality/c6031.md)|Valor de retorno ignorado|
|[C6053](../code-quality/c6053.md)|Terminação em zero da chamada|
|[C6054](../code-quality/c6054.md)|Encerramento zero ausente|
|[C6059](../code-quality/c6059.md)|Concatenação defeituosa|
|[C6063](../code-quality/c6063.md)|Argumento da cadeia de caracteres ausente para formatar função|
|[C6064](../code-quality/c6064.md)|Argumento inteiro ausente para formatar função|
|[C6066](../code-quality/c6066.md)|Argumento de ponteiro ausente para formatar função|
|[C6067](../code-quality/c6067.md)|Argumento de ponteiro de cadeia de caracteres ausente para formatar função|
|[C6101](../code-quality/c6101.md)|Retornando a memória não inicializada|
|[C6200](../code-quality/c6200.md)|O índice excede o máximo do buffer|
|[C6201](../code-quality/c6201.md)|O índice excede o máximo do buffer da pilha|
|[C6214](../code-quality/c6214.md)|Conversão de HRESULT para BOOL inválida|
|[C6215](../code-quality/c6215.md)|Conversão de BOOL para HRESULT inválida|
|[C6216](../code-quality/c6216.md)|Conversão de BOOL do compilador inserida inválida para HRESULT|
|[C6217](../code-quality/c6217.md)|Teste de HRESULT inválido com não|
|[C6220](../code-quality/c6220.md)|Comparação de HRESULT com-1 inválida|
|[C6226](../code-quality/c6226.md)|Atribuição de HRESULT inválida para-1|
|[C6230](../code-quality/c6230.md)|Uso inválido de HRESULT como booliano|
|[C6235](../code-quality/c6235.md)|Constante diferente de zero com OR lógico|
|[C6236](../code-quality/c6236.md)|OR lógico com constante diferente de zero|
|[C6237](../code-quality/c6237.md)|Zero com and lógico perde os efeitos colaterais|
|[C6242](../code-quality/c6242.md)|Desenrolamento local forçado|
|[C6248](../code-quality/c6248.md)|Criando DACL nula|
|[C6250](../code-quality/c6250.md)|Descritores de endereço não lançados|
|[C6255](../code-quality/c6255.md)|Uso desprotegido de alloca|
|[C6258](../code-quality/c6258.md)|Usando encerrar thread|
|[C6259](../code-quality/c6259.md)|Código inativo em comutador de OR-bit ou limitado|
|[C6260](../code-quality/c6260.md)|Uso de aritmética de byte|
|[C6262](../code-quality/c6262.md)|Uso excessivo de pilha|
|[C6263](../code-quality/c6263.md)|Usando alloca em loop|
|[C6268](../code-quality/c6268.md)|Parênteses ausentes na conversão|
|[C6269](../code-quality/c6269.md)|Desreferência de ponteiro ignorada|
|[C6270](../code-quality/c6270.md)|Falta argumento float para formatar a função|
|[C6271](../code-quality/c6271.md)|Argumento extra para formatar função|
|[C6272](../code-quality/c6272.md)|Argumento diferente de float para formatar a função|
|[C6273](../code-quality/c6273.md)|Argumento não inteiro para formatar a função|
|[C6274](../code-quality/c6274.md)|Argumento diferente de caractere para formatar a função|
|[C6276](../code-quality/c6276.md)|Conversão de cadeia de caracteres inválida|
|[C6277](../code-quality/c6277.md)|Chamada CreateProcess inválida|
|[C6278](../code-quality/c6278.md)|Incompatibilidade de matriz-nova escalar-exclusão|
|[C6279](../code-quality/c6279.md)|Incompatibilidade entre escalar-nova matriz-exclusão|
|[C6280](../code-quality/c6280.md)|Incompatibilidade de alocação de memória-desalocação|
|[C6281](../code-quality/c6281.md)|Precedência de relação bit-nte|
|[C6282](../code-quality/c6282.md)|A atribuição substitui o teste|
|[C6283](../code-quality/c6283.md)|Matriz primitiva-incompatibilidade de novo escalar-exclusão|
|[C6284](../code-quality/c6284.md)|Argumento de objeto inválido para formatar a função|
|[C6285](../code-quality/c6285.md)|OR lógico de constantes|
|[C6286](../code-quality/c6286.md)|Efeitos colaterais lógicos diferentes de zero|
|[C6287](../code-quality/c6287.md)|Teste redundante|
|[C6288](../code-quality/c6288.md)|Inclusão mútua sobre and lógica-and é false|
|[C6289](../code-quality/c6289.md)|A exclusão mútua sobre OR lógico é verdadeira|
|[C6290](../code-quality/c6290.md)|Precedência de NOT lógico AND bit a bit|
|[C6291](../code-quality/c6291.md)|Precedência de NOT lógico OR bit a bit|
|[C6292](../code-quality/c6292.md)|Contagens de loops acima do máximo|
|[C6293](../code-quality/c6293.md)|Contagens de loops abaixo do mínimo|
|[C6294](../code-quality/c6294.md)|Corpo do loop nunca executado|
|[C6295](../code-quality/c6295.md)|Loop infinito|
|[C6296](../code-quality/c6296.md)|Loop executado apenas uma vez|
|[C6297](../code-quality/c6297.md)|Resultado da conversão de deslocamento para tamanho maior|
|[C6299](../code-quality/c6299.md)|Comparação de campo de bits para booliano|
|[C6302](../code-quality/c6302.md)|Argumento da cadeia de caracteres inválido para formatar a função|
|[C6303](../code-quality/c6303.md)|Argumento da cadeia de caracteres larga inválido para formatar a função|
|[C6305](../code-quality/c6305.md)|Uso incompatível de tamanho e contagem|
|[C6306](../code-quality/c6306.md)|Chamada de função de argumento variável incorreta|
|[C6308](../code-quality/c6308.md)|Vazamento de realocação|
|[C6310](../code-quality/c6310.md)|Constante de filtro de exceção ilegal|
|[C6312](../code-quality/c6312.md)|Loop de execução de continuação de exceção|
|[C6314](../code-quality/c6314.md)|Precedência de or|
|[C6317](../code-quality/c6317.md)|Não é complemento|
|[C6318](../code-quality/c6318.md)|Exceção de continuação da pesquisa|
|[C6319](../code-quality/c6319.md)|Ignorado por vírgula|
|[C6324](../code-quality/c6324.md)|Cópia de cadeia de caracteres em vez de comparação de cadeia|
|[C6328](../code-quality/c6328.md)|Incompatibilidade potencial de tipo de argumento|
|[C6331](../code-quality/c6331.md)|VirtualFree Sinalizadores inválidos|
|[C6332](../code-quality/c6332.md)|VirtualFree parâmetro inválido|
|[C6333](../code-quality/c6333.md)|VirtualFree tamanho inválido|
|[C6335](../code-quality/c6335.md)|Vazamento de identificador de processo|
|[C6381](../code-quality/c6381.md)|Informações de desligamento ausentes|
|[C6383](../code-quality/c6383.md)|Estouro de buffer de contagem de elementos-contagem de bytes|
|[C6384](../code-quality/c6384.md)|Divisão do tamanho do ponteiro|
|[C6385](../code-quality/c6385.md)|Saturação de leitura|
|[C6386](../code-quality/c6386.md)|Saturação de gravação|
|[C6387](../code-quality/c6387.md)|Valor de parâmetro inválido|
|[C6388](../code-quality/c6388.md)|Valor de parâmetro inválido|
|[C6500](../code-quality/c6500.md)|Propriedade de atributo inválida|
|[C6501](../code-quality/c6501.md)|Conflito de valores de propriedades do atributo|
|[C6503](../code-quality/c6503.md)|As referências não podem ser nulas|
|[C6504](../code-quality/c6504.md)|Nulo em não ponteiro|
|[C6505](../code-quality/c6505.md)|MustCheck em nulo|
|[C6506](../code-quality/c6506.md)|Tamanho do buffer em não ponteiro ou matriz|
|[C6508](../code-quality/c6508.md)|Acesso para gravação na constante|
|[C6509](../code-quality/c6509.md)|Retorno usado em pré condição|
|[C6510](../code-quality/c6510.md)|Terminação nula em não ponteiro|
|[C6511](../code-quality/c6511.md)|MustCheck deve ser Sim ou Não|
|[C6513](../code-quality/c6513.md)|Tamanho do elemento sem tamanho do buffer|
|[C6514](../code-quality/c6514.md)|O tamanho do buffer excede o tamanho da matriz|
|[C6515](../code-quality/c6515.md)|Tamanho do buffer em não ponteiro|
|[C6516](../code-quality/c6516.md)|Nenhuma propriedade no atributo|
|[C6517](../code-quality/c6517.md)|Tamanho válido em buffer não legível|
|[C6518](../code-quality/c6518.md)|Tamanho gravável em buffer não gravável|
|[C6522](../code-quality/c6522.md)|Tipo de cadeia de caracteres de tamanho inválido|
|[C6525](../code-quality/c6525.md)|Local inatingível da cadeia de caracteres inválido|
|[C6527](../code-quality/c6527.md)|Anotação inválida: A propriedade 'NeedsRelease' não pode ser utilizada em valores de tipo void|
|[C6530](../code-quality/c6530.md)|Estilo de cadeia de caracteres de formato não reconhecido|
|[C6540](../code-quality/c6540.md)|O uso de anotações de atributo nesta função irá invalidar todas as anotações __declspec existentes na função|
|[C6551](../code-quality/c6551.md)|Especificação de tamanho inválido: expressão não analisável|
|[C6552](../code-quality/c6552.md)|Deref= ou Notref= inválidos: expressão não analisável|
|[C6701](../code-quality/c6701.md)|O valor não é um valor Sim/Não/Talvez válido|
|[C6702](../code-quality/c6702.md)|O valor não é um valor de cadeia de caracteres|
|[C6703](../code-quality/c6703.md)|O valor não é um número|
|[C6704](../code-quality/c6704.md)|Erro de Expressão de Anotação inesperada|
|[C6705](../code-quality/c6705.md)|Número esperado de argumentos para anotação não corresponde ao número de argumentos real para anotação|
|[C6706](../code-quality/c6706.md)|Erro inesperado de anotação para anotação|
|[C6995](../code-quality/c6995.md)|Falha ao salvar o arquivo de log XML|
|[C26100](../code-quality/c26100.md)|Condição de corrida|
|[C26101](../code-quality/c26101.md)|Falha ao usar a operação Interlocked corretamente|
|[C26110](../code-quality/c26110.md)|Chamador falhando ao manter bloqueio|
|[C26111](../code-quality/c26111.md)|Chamador falhando ao liberar bloqueio|
|[C26112](../code-quality/c26112.md)|O chamador não pode conter nenhum bloqueio|
|[C26115](../code-quality/c26115.md)|Falha ao liberar bloqueio|
|[C26116](../code-quality/c26116.md)|Falha ao adquirir ou manter bloqueio|
|[C26117](../code-quality/c26117.md)|Liberando bloqueio não mantido|
|[C26140](../code-quality/c26140.md)|Erro de anotação de SAL de simultaneidade|
|[C28020](../code-quality/c28020.md)|A expressão não é verdadeira nesta chamada|
|[C28021](../code-quality/c28021.md)|O parâmetro que está sendo anotado deve ser um ponteiro|
|[C28022](../code-quality/c28022.md)|As classes de função nessa função não correspondem às classes de função no typedef usado para defini-la.|
|[C28023](../code-quality/c28023.md)|A função que está sendo atribuída ou passada deve ter um \_Function \_class anotação \_ para pelo menos uma das classes|
|[C28024](../code-quality/c28024.md)|O ponteiro de função que está sendo atribuído é anotado com a classe de função, que não está contida na lista de classe (s) de função.|
|[C28039](../code-quality/c28039.md)|O tipo de parâmetro real deve corresponder exatamente ao tipo|
|[C28112](../code-quality/c28112.md)|Uma variável que é acessada por meio de uma função Interlocked sempre deve ser acessada por meio de uma função Interlocked.|
|[C28113](../code-quality/c28113.md)|Acessando uma variável local por meio de uma função Interlocked|
|[C28125](../code-quality/c28125.md)|A função deve ser chamada de dentro de um bloco try/Except|
|[C28137](../code-quality/c28137.md)|O argumento da variável deve ser uma constante (literal)|
|[C28138](../code-quality/c28138.md)|O argumento de constante deve ser variável|
|[C28159](../code-quality/c28159.md)|Considere usar outra função em vez disso.|
|[C28160](../code-quality/c28160.md)|Anotação de erro|
|[C28163](../code-quality/c28163.md)|A função nunca deve ser chamada de dentro de um bloco try/Except|
|[C28164](../code-quality/c28164.md)|O argumento está sendo passado para uma função que espera um ponteiro para um objeto (não um ponteiro para um ponteiro)|
|[C28182](../code-quality/c28182.md)|Desreferenciando ponteiro nulo. O ponteiro contém o mesmo valor NULO que outro ponteiro tinha.|
|[C28183](../code-quality/c28183.md)|O argumento pode ser um valor e é uma cópia do valor encontrado no ponteiro|
|[C28193](../code-quality/c28193.md)|A variável contém um valor que deve ser examinado|
|[C28196](../code-quality/c28196.md)|O requisito não é atendido. (A expressão não é avaliada como true.)|
|[C28202](../code-quality/c28202.md)|Referência inválida para membro não estático|
|[C28203](../code-quality/c28203.md)|Referência ambígua ao membro de classe.|
|[C28205](../code-quality/c28205.md)|\_Success \_ ou \_On \_failure \_ usados em um contexto ilegal|
|[C28206](../code-quality/c28206.md)|O operando da esquerda aponta para um struct, use '->'|
|[C28207](../code-quality/c28207.md)|O operando da esquerda é um struct, use '.'|
|[C28209](../code-quality/c28209.md)|A declaração de Symbol tem uma declaração conflitante|
|[C28210](../code-quality/c28210.md)|Anotações para o contexto __on_failure não devem estar no pré-contexto explícito|
|[C28211](../code-quality/c28211.md)|Nome esperado do contexto estático para SAL_context|
|[C28212](../code-quality/c28212.md)|Expressão de ponteiro esperada para anotação|
|[C28213](../code-quality/c28213.md)|O \_Use \_decl \_annotations anotação \_ deve ser usado para fazer referência, sem modificação, uma declaração anterior.|
|[C28214](../code-quality/c28214.md)|Os nomes do parâmetro de atributo devem ser p1...p9|
|[C28215](../code-quality/c28215.md)|O typefix não pode ser aplicado a um parâmetro que já tem um typefix|
|[C28216](../code-quality/c28216.md)|A anotação checkReturn se aplica apenas a pós-condições para o parâmetro da função específica.|
|[C28217](../code-quality/c28217.md)|Para função, o número de parâmetros para anotação não corresponde ao encontrado no arquivo|
|[C28218](../code-quality/c28218.md)|Para o parâmetro de função, o parâmetro da anotação não corresponde ao encontrado no arquivo|
|[C28219](../code-quality/c28219.md)|Membro de enumeração esperada para anotação do parâmetro na anotação|
|[C28220](../code-quality/c28220.md)|Expressão inteira esperada para anotação do parâmetro na anotação|
|[C28221](../code-quality/c28221.md)|Expressão de sequência de caracteres esperada para o parâmetro na anotação|
|[C28222](../code-quality/c28222.md)|__yes, \__no ou \__maybe esperados para anotação|
|[C28223](../code-quality/c28223.md)|O token/identificador esperado para anotação não encontrado, parâmetro|
|[C28224](../code-quality/c28224.md)|Anotação requer parâmetros|
|[C28225](../code-quality/c28225.md)|O número correto de parâmetros necessários na anotação não foi encontrado|
|[C28226](../code-quality/c28226.md)|Anotação não pode ser também um PrimOp (na declaração atual)|
|[C28227](../code-quality/c28227.md)|A anotação não pode ser também um PrimOp (veja a declaração anterior)|
|[C28228](../code-quality/c28228.md)|Parâmetro de anotação: não é possível usar tipo nas anotações|
|[C28229](../code-quality/c28229.md)|A anotação não tem suporte a parâmetros|
|[C28230](../code-quality/c28230.md)|O tipo de parâmetro não tem membro.|
|[C28231](../code-quality/c28231.md)|A anotação só é válida na matriz|
|[C28232](../code-quality/c28232.md)|pre, post ou deref não aplicados a qualquer anotação|
|[C28233](../code-quality/c28233.md)|pre, post ou deref aplicados a um bloco|
|[C28234](../code-quality/c28234.md)|__na expressão não se aplica à função atual|
|[C28235](../code-quality/c28235.md)|A função não pode ser autônoma como uma anotação|
|[C28236](../code-quality/c28236.md)|A anotação não pode ser usada em uma expressão|
|[C28237](../code-quality/c28237.md)|A anotação no parâmetro não é mais suportada|
|[C28238](../code-quality/c28238.md)|A anotação no parâmetro tem mais de um do valor, stringValue e longValue. Utilize paramn=xxx|
|[C28239](../code-quality/c28239.md)|A anotação no parâmetro tem os dois valores, stringValue e longValue; e paramn=xxx. Utilize apenas paramn=xxx|
|[C28240](../code-quality/c28240.md)|A anotação no parâmetro tem param2, mas não tem param1|
|[C28241](../code-quality/c28241.md)|A anotação para função no parâmetro não é reconhecida|
|[C28243](../code-quality/c28243.md)|A anotação para função no parâmetro requer mais desreferências do que o tipo real anotado permite|
|[C28244](../code-quality/c28244.md)|A anotação for function tem um parâmetro/anotação externa não analisável|
|[C28245](../code-quality/c28245.md)|A anotação para função anota 'este' em uma função não membro|
|[C28246](../code-quality/c28246.md)|A anotação do parâmetro para função não corresponde ao tipo do parâmetro|
|[C28250](../code-quality/c28250.md)|Anotação inconsistente para função: a instância anterior tem um erro.|
|[C28251](../code-quality/c28251.md)|Anotação inconsistente para função: esta instância tem um erro.|
|[C28252](../code-quality/c28252.md)|Anotação inconsistente para função: o parâmetro tem outras anotações nesta instância.|
|[C28253](../code-quality/c28253.md)|Anotação inconsistente para função: o parâmetro tem outras anotações nesta instância.|
|[C28254](../code-quality/c28254.md)|dynamic_cast<>() não tem suporte nas anotações|
|[C28262](../code-quality/c28262.md)|Foi encontrado um erro de sintaxe na anotação na função, para anotação|
|[C28263](../code-quality/c28263.md)|Foi encontrado um erro de sintaxe em uma anotação condicional na anotação intrínseca|
|[C28267](../code-quality/c28267.md)|Foi encontrado um erro de sintaxe nas anotações da função.|
|[C28272](../code-quality/c28272.md)|A anotação para função, parâmetro quando examinar for inconsistente com a declaração da função|
|[C28273](../code-quality/c28273.md)|Para função, os indícios são inconsistentes com a declaração da função|
|[C28275](../code-quality/c28275.md)|O parâmetro para \_Macro \_value \_ é nulo|
|[C28279](../code-quality/c28279.md)|Para símbolo, um 'início' foi encontrado sem um 'fim' correspondente|
|[C28280](../code-quality/c28280.md)|Para símbolo, um 'fim' foi encontrado sem um 'início' correspondente|
|[C28282](../code-quality/c28282.md)|Cadeias de caracteres de formato devem estar em pré-condições|
|[C28285](../code-quality/c28285.md)|Para função, erro de sintaxe no parâmetro|
|[C28286](../code-quality/c28286.md)|Para função, erro de sintaxe perto do fim|
|[C28287](../code-quality/c28287.md)|Para função, Erro de sintaxe na anotação \_At\_() (nome de parâmetro não reconhecido)|
|[C28288](../code-quality/c28288.md)|Para função, Erro de sintaxe na anotação \_At\_() (nome de parâmetro inválido)|
|[C28289](../code-quality/c28289.md)|Para função: ReadableTo ou WritableTo não tinha uma especificação de limite como parâmetro|
|[C28290](../code-quality/c28290.md)|a anotação para função contém mais Externos que o número real de parâmetros|
|[C28291](../code-quality/c28291.md)|pós null/notnull em deref nível 0 não tem sentido para a função.|
|[C28300](../code-quality/c28300.md)|Operandos da expressão de tipos incompatíveis para o operador|
|[C28301](../code-quality/c28301.md)|Não há anotações para a primeira declaração da função.|
|[C28302](../code-quality/c28302.md)|Foi encontrado um operador extra \_Deref\_ na anotação.|
|[C28303](../code-quality/c28303.md)|Foi encontrado um operador ambíguo \_Deref\_ na anotação.|
|[C28304](../code-quality/c28304.md)|Foi encontrado um operador \_Notref\_ posicionado inadequadamente aplicado ao token.|
|[C28305](../code-quality/c28305.md)|Foi encontrado um erro durante a análise de um token.|
|[C28306](../code-quality/c28306.md)|A anotação no parâmetro é obsoleta|
|[C28307](../code-quality/c28307.md)|A anotação no parâmetro é obsoleta|
|[C28350](../code-quality/c28350.md)|A anotação descreve uma situação que não é aplicável condicionalmente.|
|[C28351](../code-quality/c28351.md)|A anotação descreve onde um valor dinâmico (uma variável) não pode ser usado na condição.|
|[CA1001](../code-quality/ca1001.md)|Tipos com campos descartáveis devem ser descartáveis|
|[CA1009](../code-quality/ca1009.md)|Declarar manipuladores de eventos corretamente|
|[CA1016](../code-quality/ca1016.md)|Marcar assemblies com AssemblyVersionAttribute|
|[CA1033](../code-quality/ca1033.md)|Métodos de interface devem ser chamados por tipos filho|
|[CA1049](../code-quality/ca1049.md)|Tipos com recursos nativos devem ser descartáveis|
|[CA1060](../code-quality/ca1060.md)|Mova P/Invokes para a classe NativeMethods|
|[CA1061](../code-quality/ca1061.md)|Não ocultar métodos de classe base|
|[CA1063](../code-quality/ca1063.md)|Implementar IDisposable corretamente|
|[CA1065](../code-quality/ca1065.md)|Não acionar exceções em locais inesperados|
|[CA1301](../code-quality/ca1301.md)|Evitar aceleradores duplicados|
|[CA1400](../code-quality/ca1400.md)|Deve haver pontos de entrada P/Invoke|
|[CA1401](../code-quality/ca1401.md)|P/Invokes não devem ser visíveis|
|[CA1403](../code-quality/ca1403.md)|Tipos de layout automático não devem ser visíveis no COM|
|[CA1404](../code-quality/ca1404.md)|Chamar GetLastError imediatamente após P/Invoke|
|[CA1405](../code-quality/ca1405.md)|Tipos base de tipo visível no COM devem ser visíveis no COM|
|[CA1410](../code-quality/ca1410.md)|Métodos de registro COM devem ser correspondidos|
|[CA1415](../code-quality/ca1415.md)|Declarar P/Invokes corretamente|
|[CA1821](../code-quality/ca1821.md)|Remover finalizadores vazios|
|[CA1900](../code-quality/ca1900.md)|Campos de tipo de valor devem ser portáteis|
|[CA1901](../code-quality/ca1901.md)|Declarações P/Invoke devem ser portáteis|
|[CA2002](../code-quality/ca2002.md)|Não bloquear objetos com identidade fraca|
|[CA2100](../code-quality/ca2100.md)|Examinar consultas SQL em busca de vulnerabilidades de segurança|
|[CA2101](../code-quality/ca2101.md)|Especificar marshaling para argumentos de cadeias de caracteres P/Invoke|
|[CA2108](../code-quality/ca2108.md)|Examinar a segurança declarativa em tipos de valor|
|[CA2111](../code-quality/ca2111.md)|Ponteiros não devem ser visíveis|
|[CA2112](../code-quality/ca2112.md)|Tipos protegidos não devem expor campos|
|[CA2114](../code-quality/ca2114.md)|A segurança do método deve ser um superconjunto do tipo|
|[CA2116](../code-quality/ca2116.md)|Métodos APTCA devem chamar somente métodos APTCA|
|[CA2117](../code-quality/ca2117.md)|Tipos APTCA devem estender somente tipos base APTCA|
|[CA2122](../code-quality/ca2122.md)|Não expor indiretamente métodos com demandas de link|
|[CA2123](../code-quality/ca2123.md)|As demandas de link de substituição devem ser idênticas à base|
|[CA2124](../code-quality/ca2124.md)|Encapsular cláusulas finally vulneráveis em try externo|
|[CA2126](../code-quality/ca2126.md)|As demandas de link de tipo exigem demandas de herança|
|[CA2131](../code-quality/ca2131.md)|Tipos críticos de segurança podem não participar da equivalência de tipo|
|[CA2132](../code-quality/ca2132.md)|Construtores padrão devem ser pelo menos tão críticos quanto construtores padrão do tipo base|
|[CA2133](../code-quality/ca2133.md)|Representantes devem ser associados a métodos com transparência consistente|
|[CA2134](../code-quality/ca2134.md)|Os métodos devem manter uma transparência consistente durante a substituição dos métodos base|
|[CA2137](../code-quality/ca2137.md)|Métodos transparentes devem conter apenas a IL verificável|
|[CA2138](../code-quality/ca2138.md)|Métodos transparentes não devem chamar métodos com o atributo SuppressUnmanagedCodeSecurity|
|[CA2140](../code-quality/ca2140.md)|O código transparente não deve referenciar itens críticos de segurança|
|[CA2141](../code-quality/ca2141.md)|Métodos transparentes não devem satisfazer LinkDemands|
|[CA2146](../code-quality/ca2146.md)|Os tipos devem ser pelo menos tão críticos quanto seus tipos base e interfaces|
|[CA2147](../code-quality/ca2147.md)|Métodos transparentes podem não usar declarações de segurança|
|[CA2149](../code-quality/ca2149.md)|Métodos transparentes não devem chamar código nativo|
|[CA2200](../code-quality/ca2200.md)|Relançar para preservar detalhes da pilha|
|[CA2202](../code-quality/ca2202.md)|Não descartar objetos várias vezes|
|[CA2207](../code-quality/ca2207.md)|Inicializar campos estáticos de tipo de valor em linha|
|[CA2212](../code-quality/ca2212.md)|Não marcar componentes atendidos com WebMethod|
|[CA2213](../code-quality/ca2213.md)|Campos descartáveis devem ser descartados|
|[CA2214](../code-quality/ca2214.md)|Não chamar métodos substituíveis em construtores|
|[CA2216](../code-quality/ca2216.md)|Tipos descartáveis devem declarar o finalizador|
|[CA2220](../code-quality/ca2220.md)|Os finalizadores devem chamar o finalizador de classe base|
|[CA2229](../code-quality/ca2229.md)|Implementar construtores de serialização|
|[CA2231](../code-quality/ca2231.md)|Sobrecarregar operador equals ao substituir ValueType.Equals|
|[CA2232](../code-quality/ca2232.md)|Marcar pontos de entrada do Windows Forms com STAThread|
|[CA2235](../code-quality/ca2235.md)|Marcar todos os campos não serializáveis|
|[CA2236](../code-quality/ca2236.md)|Chamar métodos da classe base em tipos ISerializable|
|[CA2237](../code-quality/ca2237.md)|Marcar tipos ISerializable com SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|Implementar métodos de serialização corretamente|
|[CA2240](../code-quality/ca2240.md)|Implementar ISerializable corretamente|
|[CA2241](../code-quality/ca2241.md)|Fornecer argumentos corretos para métodos de formatação|
|[CA2242](../code-quality/ca2242.md)|Testar para NaN corretamente|
