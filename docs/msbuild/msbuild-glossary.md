---
title: Glossário do MSBuild
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f767d8e4-24d8-4803-80eb-e857202dbe2c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3d5f9e402750978b1201c6b2a5b1ef0659e8789
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593662"
---
# <a name="msbuild-glossary"></a>Glossário do MSBuild

Esses termos são usados para descrever o MSBuild (Microsoft Build Engine) e seus componentes.

## <a name="glossary"></a>Glossário

AssemblyFoldersEx\
Um local de Registro em que os fornecedores de terceiros armazenam caminhos para cada versão da estrutura que dão suporte ao local em que a resolução do tempo de design pode consultar para localizar assemblies de referência.

envio em lote\
O envio em lote significa dividir itens em categorias diferentes, conhecidas como *lotes*, com base nos metadados do item e, em seguida, executar um destino ou uma tarefa por vez usando cada lote. O envio em lote é o equivalente do MSBuild para o constructo --loop. Para obter mais informações, consulte [Envio em lote](../msbuild/msbuild-batching.md).

escopo de build\
O escopo de build descreve um objeto do MSBuild, por exemplo, uma propriedade global, que é potencialmente visível para um projeto e quaisquer projetos filho que são criados em um build de vários projetos.

projeto filho\
Consulte *projeto, filho*.

condição\
Muitos elementos do MSBuild podem ser definidos condicionalmente; ou seja, o atributo `Condition` aparece no elemento. O conteúdo dos elementos condicionais é ignorado a menos que a condição seja avaliada como `true`. Para obter mais informações, consulte [Condições](../msbuild/msbuild-conditions.md).

definição, item\
Consulte *definição de item*.

item emit\
Durante a fase de execução de um build, os itens podem ser criados ou modificados por tarefas que têm elementos `Output` filho que têm o atributo `ItemName`. Diz-se que a tarefa "emite" os novos itens.

propriedade emit\
Durante a fase de execução de um build, as propriedades podem ser criadas ou modificadas por tarefas que têm elementos `Output` filho que têm o atributo `PropertyName`. Diz-se que a tarefa "emite" a nova propriedade.

fase de avaliação\
A avaliação é a primeira fase de um build de projeto. Todas as propriedades e os itens são avaliados na ordem em que aparecem no projeto. Os projetos importados são avaliados conforme são encontrados no projeto. Destinos e tarefas não serão executados até a fase de execução e quaisquer propriedades ou itens que eles declarariam ou emitiriam serão ignorados durante a avaliação.

fase de execução\
A execução é a segunda fase de um build de projeto. Os destinos selecionados são criados e as tarefas são executadas. As propriedades e os itens podem ser criados ou modificados em comparação com seus valores de avaliação.

função, propriedade\
Consulte *função de propriedade*.

função, item\
Consulte a função de item.

item\
Os itens são entradas no sistema de build e são agrupados em tipos de item com base em seus nomes de elemento. Normalmente, os itens representam arquivos. Como os itens são nomeados pelo tipo de item ao qual pertencem, os termos *item* e *valor de item* podem ser usados alternadamente. Para obter mais informações, consulte [Itens](../msbuild/msbuild-items.md).

definição de item\
Os grupos de definição de item contêm as definições de item que adicionam metadados padrão a qualquer tipo de item. Como metadados conhecidos, os metadados padrão estão associados a todos os itens do tipo de item especificado. Os metadados padrão podem ser substituídos explicitamente em uma definição de item. Para obter mais informações, confira [Definições de item](../msbuild/item-definitions.md).

função de item\
As funções de item obtêm informações sobre os itens no projeto. Essas funções simplificam a obtenção de itens Distinct() e são mais rápidas do que executar loop nos itens. Há funções para manipular cadeias de caracteres e caminhos de item. Para saber mais, confira [Funções de item](../msbuild/item-functions.md).

metadados de item\
Consulte *metadados, item*.

tipo de item\
Os tipos de item são listas nomeadas de itens que podem ser usados como parâmetros para tarefas. As tarefas usam os valores do item para executar as etapas do processo de build. Para obter mais informações, consulte [Itens](../msbuild/msbuild-items.md).

metadados, item\
Os metadados de item são uma coleção de pares nome-valor associados a um item. Os metadados fornecem informações descritivas para o item e são opcionais, com exceção de metadados bem conhecidos. Para obter mais informações, consulte [Itens](../msbuild/msbuild-items.md).

metadados, conhecidos\
Os metadados conhecidos são metadados de item somente leitura que são inicializados usando um valor predefinido. Os metadados conhecidos fornecem informações descritivas para um item que faz referência a um arquivo. Por exemplo, o valor dos metadados conhecidos chamado `FullPath` é o caminho completo do arquivo referenciado. Para obter mais informações, consulte [Itens](../msbuild/msbuild-items.md).

multiplataforma\
A capacidade de um projeto de aplicativo ou de assembly de direcionar vários CLRs e estruturas diferentes do MSBuild e do Visual Studio.

perfil\
Um subconjunto da estrutura completa. Ele é usado para minimizar a quantidade que precisa ser baixado para um computador.

arquivo de projeto\
Um arquivo de projeto contém o script MSBuild que controla o build. Normalmente, os arquivos de projeto têm uma extensão de arquivo que termina com *proj*, como *.csproj* ou *.vbproj*. Os arquivos de projeto podem importar arquivos de propriedade e de destino.

propriedade\
Uma propriedade é um par chave-valor que é usado para controlar o processo de build. Para obter mais informações, confira [Propriedades do MSBuild](../msbuild/msbuild-properties.md).

propriedade, ambiente\
Uma propriedade de ambiente é uma propriedade que é inicializada automaticamente para o valor de uma variável de ambiente do sistema que tem o mesmo nome. Para obter mais informações, confira [Propriedades do MSBuild](../msbuild/msbuild-properties.md).

arquivo de propriedade\
Um arquivo de propriedade é um arquivo de projeto que contém principalmente grupos de propriedade e grupos de itens que orientam o build. Por convenção, ele tem a extensão de arquivo *.props*. Normalmente, os arquivos de propriedade são importados no início dos arquivos de projeto associados.

propriedade, função\
Uma função de propriedade é uma propriedade do sistema ou um método que pode ser usado para avaliar scripts do MSBuild. Os métodos de propriedade podem ser usados para ler a hora do sistema, comparar cadeias de caracteres, combinar expressões regulares e executar outras ações. Para obter mais informações, confira [Funções de propriedade](../msbuild/property-functions.md).

função de propriedade, aninhada\
As funções de propriedade podem ser combinadas para formar funções mais complexas. Por exemplo,

 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`

Para obter mais informações, confira [Funções de propriedade](../msbuild/property-functions.md).

propriedade, global\
Uma propriedade global é um par chave-valor que é usado para controlar o processo de build. As propriedades globais são definidas em um prompt de comando ou usando o atributo `Properties` de uma [tarefa do MSBuild](../msbuild/msbuild-task.md) e não podem ser modificadas durante a fase de avaliação de um build. Para obter mais informações, confira [Propriedades do MSBuild](../msbuild/msbuild-properties.md).

propriedade, local\
Uma propriedade local é um par chave-valor que é usado para controlar o processo de build. Este termo é usado apenas para distinguir uma propriedade que não é uma propriedade global.

propriedade, registro\
Uma propriedade de Registro tem um valor que é definido usando uma sintaxe especial que lê o valor de uma subchave de Registro do sistema. Para obter mais informações, confira [Propriedades do MSBuild](../msbuild/msbuild-properties.md).

propriedade, reservada\
Uma propriedade reservada é um par chave-valor que é usado para controlar o processo de build. As propriedades reservadas são inicializadas automaticamente com valores predefinidos. Para obter mais informações, confira [Propriedades do MSBuild](../msbuild/msbuild-properties.md).

escopo de projeto\
O escopo do projeto descreve um objeto do MSBuild, por exemplo, uma propriedade local, que é visível somente no arquivo de projeto e em todos os projetos que ele importa.

projeto, filho\
Um projeto filho é criado pela tarefa do MSBuild durante o build do projeto. Esse novo projeto é um filho do projeto que contém ou importa o destino que contém a tarefa do MSBuild. O projeto filho herda as propriedades globais do projeto pai, a menos que elas tenham sido modificadas pelo atributo `Properties`.

lista redist\
Lista de redistribuição: a lista de assemblies que corresponde a uma determinada estrutura.

assembly de referência\
Um assembly que é usado durante o tempo de design para criar um aplicativo. Um assembly de referência pode ter o código real e as interfaces privadas removidos dele, deixando apenas os metadados e as interfaces públicas.

propriedade de registro\
Consulte *propriedade, Registro*.

destino\
Um destino agrupa tarefas em uma ordem específica e expõe seções do arquivo de projeto como pontos de entrada para o processo de build. Para obter mais informações, consulte [Destinos](../msbuild/msbuild-targets.md).

destino, criar\
Consulte destino, execução.

destino, avaliar\
Devido à compilação incremental, os destinos devem ser analisados quanto a possíveis alterações nas propriedades e nos itens. Mesmo se o destino for ignorado, essas alterações deverão ser feitas. Avaliar um destino significa executar essa análise e fazer essas alterações. Para obter mais informações, confira [Builds incrementais](../msbuild/incremental-builds.md).

destino, executar\
Executar um destino significa avaliá-lo e executar todas as tarefas que não têm condições ou cujas condições são avaliadas como true. Durante a compilação incremental, os destinos podem ser ignorados ou executados, mas eles são sempre avaliados. Para obter mais informações, consulte destino, avaliação.

destino, execução\
Um destino que tem uma condição avaliada como false não é executado, ou seja, não tem nenhum efeito no build. Os destinos em execução são executados ou ignorados. Em ambos os casos, o destino é avaliado. Para obter mais informações, consulte destino, avaliação.

destino, ignorar\
Se a compilação incremental determina que todos os arquivos de saída estão atualizados, então o destino é ignorado, isto é, o destino é avaliado, mas as tarefas dentro do destino não são executadas. Para obter mais informações, consulte destino, avaliação.

moniker da estrutura de destino\
Um nome que descreve a estrutura (como .NET Framework, Silverlight etc.), a versão e o perfil (como Cliente, Servidor etc.) que você deseja usar como destino.

direcionamento de pacote\
A lista de assemblies que são distribuídos com uma determinada estrutura e o conjunto de assemblies de referência para essa estrutura.

arquivo de destino\
Um arquivo de destino é um arquivo de projeto que contém, em grande parte, destinos e tarefas que orientam o build. Por convenção, ele tem a extensão de arquivo *.targets*. Normalmente, os arquivos de destino são importados no fim dos arquivos de projeto associados.

tarefa\
As tarefas são unidades de código executável que os projetos [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] usam para executar operações de build. Por exemplo, uma tarefa pode compilar os arquivos de entrada ou executar uma ferramenta externa. Para obter mais informações, consulte [Tarefas](../msbuild/msbuild-tasks.md).

transformação\
Uma transformação é uma conversão individual de uma coleção de item para outra. Além de habilitar um projeto para converter as coleções de itens, uma transformação permite que um destino identifique um mapeamento direto entre suas entradas e saídas. Para obter mais informações, consulte [Transformações](../msbuild/msbuild-transforms.md).

metadados conhecidos\
Consulte *metadados, conhecidos*.

## <a name="see-also"></a>Veja também

- [MSBuild](../msbuild/msbuild.md)
