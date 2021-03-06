---
title: Depurando um modelo de texto T4
description: Para depurar um modelo de texto de tempo de design, salve o arquivo de modelo de texto e escolha Depurar modelo T4 no menu de atalho do arquivo em Gerenciador de Soluções.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, troubleshooting
- text templates, debugging
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b197fd52972162acbc6e7d6882507f943b2a560c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935346"
---
# <a name="debugging-a-t4-text-template"></a>Depurando um modelo de texto T4
Você pode definir pontos de interrupção em modelos de texto. Para depurar um modelo de texto de tempo de design, salve o arquivo de modelo de texto e escolha **depurar modelo T4** no menu de atalho do arquivo em Gerenciador de soluções. Para depurar um modelo de texto de tempo de execução, basta depurar o aplicativo ao qual ele pertence.

 Para depurar um modelo de texto, você deve entender as etapas do processo de transformação de modelo. Tipos diferentes de erros podem ocorrer em cada etapa. As etapas são as seguintes.

|Etapa|Modelo de tempo de design: quando ocorre|Modelo de tempo de execução: quando ocorre|
|-|-|-|
|O código é gerado a partir do modelo de texto.<br /><br /> Erros em diretivas ou marcas não correspondentes ou desordenadas `<#...#>` .|Quando você salva o modelo ou invoca a transformação de texto.|Quando você salva o modelo ou invoca a transformação de texto.|
|O código gerado é compilado.<br /><br /> Erros de compilação no seu código de modelo.|Imediatamente após a etapa anterior.|Junto com o código do aplicativo.|
|Execuções de código.<br /><br /> Erros de tempo de execução no seu código de modelo.|Imediatamente após a etapa anterior.|Quando o aplicativo é executado e invoca o código do modelo.|

 Na maioria dos casos, os números de linha no código do modelo são fornecidos no relatório de erros. Quando o relatório de erros se refere a um nome de arquivo temporário, a causa usual é um colchete incompatível no código do modelo de texto.

 Você pode definir pontos de interrupção em modelos de texto e depurar da maneira usual.

## <a name="common-errors-and-fixes"></a>Erros e correções comuns
 A tabela a seguir lista os erros mais comuns e suas correções.

|Mensagem de erro|Descrição|Solução|
|-|-|-|
|Falha ao carregar a classe base ' {0} ' da qual a classe de transformação é herdada.|Ocorre se você não encontrar a classe base especificada no `inherits` parâmetro em uma diretiva de modelo. A mensagem fornece o número de linha da diretiva de modelo.|Verifique se a classe especificada existe e se o assembly em que ela existe está especificado em uma diretiva de assembly.|
|Falha ao resolver o texto de inclusão para o arquivo:{0}|Ocorre quando você não pode localizar um modelo incluído. A mensagem fornece o nome do arquivo de inclusão solicitado.|Verifique se o caminho do arquivo é relativo ao caminho do modelo original ou se o arquivo está em um local registrado com o host ou se há um caminho completo para o arquivo.|
|Erros foram gerados ao inicializar o objeto de transformação. A transformação não será executada.|Ocorre quando o ' Initialize () ' da classe de transformação falhou ou retornou false.|O código na função Initialize () vem da classe de transformação base especificada na \<#@template#> diretiva e dos processadores de diretiva. O erro que causou a inicialização falhar provavelmente está na lista de erros. Investigue o motivo da falha. Você pode examinar o código gerado real para Initialize () seguindo os procedimentos para depurar um modelo.|
|O assembly ' {0} ' para o processador de diretiva ' {1} ' não recebeu o conjunto de permissões FullTrust. Somente os assemblies confiáveis têm permissão para fornecer processadores de diretiva. Esse processador de diretiva não será carregado.|Ocorre quando o sistema não concede permissões FullTrust a um assembly que contém um processador de diretiva. A mensagem fornece o nome do assembly e o nome do processador de diretiva.|Certifique-se de usar apenas assemblies confiáveis no computador local.|
|O caminho ' {0} ' deve ser local para este computador ou parte de sua zona confiável.|Ocorre quando uma diretiva ou diretiva de assembly faz referência a um arquivo que não está no computador local ou na zona confiável da rede.|Certifique-se de que o diretório onde as diretivas de diretiva ou de assembly estão localizadas esteja em sua zona confiável. Você pode adicionar um diretório de rede à sua zona confiável por meio do Internet Explorer.|
|Vários erros de sintaxe, como "catch ' inválido de token '" ou "um namespace não pode conter diretamente Membros"|Número excessivo de chaves de fechamento no seu código de modelo. O compilador está confuso com o código de geração padrão.|Verifique o número de chaves de fechamento e colchetes dentro dos delimitadores de código.|
|Loops ou condicionais não compilados ou executados corretamente. Por exemplo, `<#if (i>10)#> Number is: <#= i #>`.<br /><br /> Esse código sempre gera o valor de i. Somente "número é:" é condicional.|Em C#, sempre use chaves para circundar blocos de texto inseridos em instruções de controle.|Adicionar chaves: `<#if (i>10) { #>    Number is: <#= i #><# } #>` .|
|"Expressão muito complexa" ao processar um modelo em tempo de design ou compilar um modelo de tempo de execução (pré-processado).<br /><br /> O Visual Studio para de funcionar ao tentar inspecionar o código gerado por um modelo de tempo de execução.|O bloco de texto é muito longo. O T4 converte blocos de texto em uma expressão de concatenação de cadeia de caracteres, com um literal de cadeia de caracteres para cada linha de modelo. Blocos de texto muito longos podem overstep os limites de tamanho do compilador.|Divida o bloco de texto longo com um bloco de expressão, como:<br /><br /> `<#= "" #>`|

## <a name="warning-descriptions-and-fixes"></a>Descrições e correções de aviso
 A tabela a seguir lista os avisos mais comuns em conjunto com correções, se disponíveis.

|Mensagem de aviso|Descrição|Solução|
|-|-|-|
|O carregamento do arquivo de inclusão ' {0} ' retornou uma cadeia de caracteres nula ou vazia.|Ocorre se um arquivo de modelo de texto incluído estiver em branco. A mensagem fornece o nome de arquivo do arquivo incluído.|Remova a diretiva include ou verifique se o arquivo tem algum conteúdo.|
|Compilando transformação:|Precede essa cadeia de caracteres para todos os erros ou avisos provenientes do compilador ao compilar a transformação. Essa cadeia de caracteres significa que o compilador gerou um erro ou aviso.|Se você tiver um problema ao localizar a DLL, talvez seja necessário fornecer o caminho completo ou um nome forte totalmente qualificado se a DLL estiver no GAC.|
|O parâmetro ' {0} ' já existe na diretiva. O parâmetro duplicado será ignorado.|Ocorre quando um parâmetro é especificado mais de uma vez em uma diretiva. A mensagem fornece o nome do parâmetro e o número de linha da diretiva.|Remova a especificação de parâmetro duplicada.|
|Erro ao carregar o arquivo de inclusão ' {0} '. A diretiva include será ignorada.|Ocorre quando você não pode localizar um arquivo especificado em uma `include` diretiva. A mensagem fornece o nome do arquivo e o número de linha da diretiva.|Certifique-se de que o arquivo de inclusão exista no mesmo diretório que o arquivo de modelo de texto original ou em um dos diretórios de inclusão registrados no host.|
|Uma classe base inválida foi especificada para a classe de transformação. A classe base deve derivar de Microsoft. VisualStudio. TextTemplating. TextTransformation.|Ocorre quando o `inherits` parâmetro em uma diretiva de modelo especifica uma classe que não herda de `TextTransformation` . A mensagem fornece o número de linha da diretiva de modelo.|Especifique uma classe derivada de `TextTransformation` .|
|Uma cultura inválida foi especificada na diretiva ' template '. A cultura deve estar no formato "XX-XX". A cultura invariável será usada.|Ocorre quando o parâmetro Culture em uma diretiva de modelo é especificado incorretamente. A mensagem fornece o número de linha da diretiva de modelo.|Altere o parâmetro Culture para uma cultura válida no formato "XX-XX".|
|Um valor de depuração inválido ' {0} ' foi especificado na diretiva de modelo. O valor de depuração deve ser "true" ou "false". O padrão de "false" será usado.|Ocorre quando o `debug` parâmetro em uma diretiva de modelo é especificado incorretamente. A mensagem fornece o número de linha da diretiva de modelo.|Defina o parâmetro de depuração como "true" ou "false".|
|Um valor de HostSpecific inválido ' {0} ' foi especificado na diretiva de modelo. O valor de HostSpecific deve ser "true" ou "false". O padrão de "false" será usado.|Ocorre quando o parâmetro específico do host em uma `template` diretiva é especificado incorretamente. A mensagem fornece o número de linha da diretiva de modelo.|Defina o parâmetro específico do host como "true" ou "false".|
|Uma linguagem inválida ' {0} ' foi especificada na diretiva ' template '. O idioma deve ser "C#" ou "VB". O valor padrão de "C#" será usado.|Ocorre quando um idioma sem suporte é especificado na `template` diretiva. Somente "C#" ou "VB" são permitidos (não diferencia maiúsculas de minúsculas). A mensagem fornece o número de linha da diretiva de modelo.|Defina o `language` parâmetro na diretiva de modelo como "C#" ou "vb".|
|Várias diretivas de saída foram encontradas no modelo. Todos, exceto o primeiro, serão ignorados.|Ocorre quando várias `output` diretivas são especificadas em um arquivo de modelo. A mensagem fornece o número de linha da diretiva de saída duplicada.|Remova as `output` diretivas duplicadas.|
|Foram encontradas várias diretivas de modelo no modelo. Todos, exceto o primeiro, serão ignorados. Vários parâmetros para a diretiva de modelo devem ser especificados dentro de uma diretiva de modelo.|Ocorre se você especificar várias `template` diretivas dentro de um arquivo de modelo de texto (incluindo arquivos incluídos). A mensagem fornece o número de linha da diretiva de modelo duplicada.|Agregar as `template` diretivas diferentes em uma `template` diretiva.|
|Nenhum processador foi especificado para uma diretiva chamada ' {0} '. A diretiva será ignorada.|Ocorre se você especificar uma `custom` diretiva, mas não fornecer um `processor` atributo. A mensagem fornece o nome da diretiva e o número da linha.|Forneça um `processor` atributo com o nome do `directive` processador para a diretiva.|
|Não foi possível encontrar um processador chamado ' {0} ' para a diretiva chamada ' {1} '. A diretiva será ignorada.|Ocorre quando o sistema não consegue localizar o `directive` processador especificado em uma `custom` diretiva. A mensagem fornece o nome da diretiva, o nome do processador e o número de linha da diretiva.|Defina o `processor` atributo na diretiva como o nome do processador de diretiva.|
|Um parâmetro obrigatório ' {0} ' para a diretiva ' {1} ' não foi encontrado. A diretiva será ignorada.|Ocorre quando o sistema não fornece um parâmetro de diretiva necessário. A mensagem fornece o nome do parâmetro ausente, o nome da diretiva e o número da linha.|Forneça o parâmetro ausente.|
|O processador chamado ' {0} ' não oferece suporte à diretiva chamada ' {1} '. A diretiva será ignorada.|Ocorre quando um processador de diretiva não dá suporte a uma diretiva. A mensagem fornece o nome e o número de linha da diretiva incorreta junto com o nome do processador de diretiva.|Corrija o nome da diretiva.|
|A diretiva include para o arquivo ' {0} ' causa um loop infinito.|Exibido se as diretivas de inclusão circular forem especificadas (por exemplo, o arquivo A inclui o arquivo B, que inclui o arquivo A).|Não especifique as diretivas de inclusão circular.|
|Executando transformação:|Precede essa cadeia de caracteres para todos os erros ou avisos gerados durante a execução da transformação.|Não aplicável.|
|Uma marca de início ou de fim inesperada foi encontrada em um bloco. Certifique-se de que você não incorretamente digitou uma marca de início ou de término e que você não tem nenhum bloco aninhado no modelo.|Exibido quando você tem um inesperado \<# or #> . Ou seja, se você tiver um quando não houver uma \<# after another open tag that has not been closed, or you have a #> marca aberta não fechada antes dela. A mensagem fornece o número de linha da marca incompatível.|Remova a marca de início ou de fim incompatível ou use um caractere de escape.|
|Uma diretiva foi especificada no formato incorreto. A diretiva será ignorada. Especifique a diretiva no formato `<#@ name [parametername="parametervalue"]*  #>`|Exibido pelo analisador se uma diretiva não for especificada no formato correto. A mensagem fornece o número de linha da diretiva incorreta.|Certifique-se de que todas as diretivas estejam no formato `<#@ name [parametername="parametervalue"]*  #>` . Para obter mais informações, consulte [diretivas de modelo de texto T4](../modeling/t4-text-template-directives.md).|
|Falha ao carregar o assembly ' {0} ' para o processador de diretiva registrado ' {1} '<br /><br /> {2}|Ocorre quando um processador de diretiva não pôde ser carregado pelo host. A mensagem identifica o assembly fornecido para o processador de diretiva e o nome do processador de diretiva.|Verifique se o processador de diretivas está registrado corretamente e se o assembly existe.|
|Falha ao encontrar o tipo ' {0} ' no assembly ' {1} ' para o processador de diretiva registrado ' {2} '<br /><br /> {3}|Ocorre quando um tipo de processador de diretiva não pode ser carregado a partir de seu assembly. A mensagem fornece o nome do tipo, assembly e processador de diretiva.|O vshost localiza informações do processador de diretivas (nome, assembly e tipo) no registro. Verifique se o processador de diretivas está registrado corretamente e se o tipo existe no assembly.|
|Houve um problema ao carregar o assembly ' {0} '|Ocorre quando há um problema ao carregar um assembly. A mensagem fornece o nome do assembly.|Você pode especificar assemblies a serem carregados em \<@#assembly#> diretivas e por processadores de diretiva. A mensagem de erro que segue essa cadeia de caracteres deve fornecer mais dados sobre o motivo da falha no carregamento do assembly.|
|Houve um problema ao criar e inicializar o processador para uma diretiva chamada ' {1} '. O tipo do processador é {0} . A diretiva será ignorada.|Ocorre quando o sistema não pôde criar ou inicializar um processador de diretiva. A mensagem fornece o nome e o número de linha da diretiva e o tipo do processador.|Certifique-se de usar o processador de diretiva correto e de que o processador de diretivas tenha um construtor público padrão. Caso contrário, use as opções de depuração para descobrir por que o método Initialize () do processador de diretivas está falhando. Para obter mais informações, consulte [Solucionando problemas de modelos de texto](../modeling/debugging-a-t4-text-template.md).|
|Uma exceção foi lançada durante o processamento de uma diretiva chamada ' {0} '.|Ocorre quando um processador de diretiva gera uma exceção ao processar uma diretiva.|Verifique se os parâmetros para o processador de diretiva estão corretos.|
|O host lançou uma exceção ao tentar resolver a referência de assembly ' {0} '.|Ocorre quando o host gera uma exceção ao tentar resolver uma referência de assembly. A mensagem fornece a cadeia de caracteres de referência do assembly.|Referências de assembly vêm de \<@#assembly#> diretivas e de processadores de diretiva. Certifique-se de que o parâmetro ' name ' fornecido no parâmetro de assembly esteja correto.|
|Tentativa de especificar o valor sem suporte {1} ' {0} ' para a diretiva {2}|Ocorre pelo RequiresProvidesDirectiveProcessor (todos os nossos processadores de diretiva gerados derivam dele), quando você fornece um argumento Requires sem suporte ou fornece.|Certifique-se de que os nomes nos pares nome = ' valor ' fornecidos no requer e fornece parâmetros estão corretos.|
