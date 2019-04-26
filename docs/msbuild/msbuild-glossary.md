---
title: Glossário do MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f767d8e4-24d8-4803-80eb-e857202dbe2c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f074bf7b5c7077b1c4808d7d3035be0c6366d526
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62842468"
---
# <a name="msbuild-glossary"></a>Glossário do MSBuild
Esses termos são usados para descrever o MSBuild (Microsoft Build Engine) e seus componentes.

## <a name="glossary"></a>Glossário
 AssemblyFoldersEx Um local de Registro em que os fornecedores de terceiros armazenam caminhos para cada versão da estrutura para a qual dão suporte e em que a resolução em tempo de design pode procurar para encontrar assemblies de referência.

 envio em lote O envio em lote significa dividir itens em categorias diferentes, conhecidas como *lotes*, com base nos metadados do item e, em seguida, executar um destino ou uma tarefa por vez usando cada lote. O envio em lote é o equivalente do MSBuild para o constructo --loop. Para obter mais informações, consulte [Envio em lote](../msbuild/msbuild-batching.md).

 escopo do build O escopo do build descreve um objeto do MSBuild, por exemplo, uma propriedade global, que é potencialmente visível para um projeto e os projetos filho criados em um build de vários projetos.

 projeto filho Confira *projeto, filho*.

 condição Muitos elementos do MSBuild podem ser definidos condicionalmente; ou seja, o atributo `Condition` aparece no elemento. O conteúdo dos elementos condicionais é ignorado a menos que a condição seja avaliada como `true`. Para obter mais informações, consulte [Condições](../msbuild/msbuild-conditions.md).

 definição, item, Confira *definição de item*.

 emitir item Durante a fase de execução de um build, os itens podem ser criados ou modificados por tarefas que têm elementos `Output` filho contendo o atributo `ItemName`. Diz-se que a tarefa "emite" os novos itens.

 emitir propriedade Durante a fase de execução de um build, as propriedades podem ser criadas ou modificadas por tarefas que têm elementos `Output` filho contendo o atributo `PropertyName`. Diz-se que a tarefa "emite" a nova propriedade.

 fase de avaliação A avaliação é a primeira fase de um build de projeto. Todas as propriedades e os itens são avaliados na ordem em que aparecem no projeto. Os projetos importados são avaliados conforme são encontrados no projeto. Destinos e tarefas não serão executados até a fase de execução e quaisquer propriedades ou itens que eles declarariam ou emitiriam serão ignorados durante a avaliação.

 fase de execução A execução é a segunda fase de um build de projeto. Os destinos selecionados são criados e as tarefas são executadas. As propriedades e os itens podem ser criados ou modificados em comparação com seus valores de avaliação.

 função, propriedade, Confira *função de propriedade*.

 função, item Confira função de item.

 item Os itens são entradas no sistema de build e são agrupados em tipos de item com base em seus nomes de elemento. Normalmente, os itens representam arquivos. Como os itens são nomeados pelo tipo de item ao qual pertencem, os termos *item* e *valor de item* podem ser usados alternadamente. Para obter mais informações, consulte [Itens](../msbuild/msbuild-items.md).

 definição de item Os grupos de definição de item contêm definições de item que adicionam metadados padrão a qualquer tipo de item. Como metadados conhecidos, os metadados padrão estão associados a todos os itens do tipo de item especificado. Os metadados padrão podem ser substituídos explicitamente em uma definição de item. Para obter mais informações, confira [Definições de item](../msbuild/item-definitions.md).

 função de item As funções de item obtêm informações sobre os itens no projeto. Essas funções simplificam a obtenção de itens Distinct() e são mais rápidas do que executar loop nos itens. Há funções para manipular cadeias de caracteres e caminhos de item. Para obter mais informações, confira [Funções de item](../msbuild/item-functions.md)

 metadados de item Confira *metadados, item*.

 tipo de item Os tipos de item são listas nomeadas de itens que podem ser usados como parâmetros para tarefas. As tarefas usam os valores do item para executar as etapas do processo de build. Para obter mais informações, consulte [Itens](../msbuild/msbuild-items.md).

 metadados, item Os metadados de item são uma coleção de pares nome-valor associados a um item. Os metadados fornecem informações descritivas para o item e são opcionais, com exceção de metadados bem conhecidos. Para obter mais informações, consulte [Itens](../msbuild/msbuild-items.md).

 metadados, conhecidos Os metadados conhecidos são metadados de item somente leitura que são inicializados usando um valor predefinido. Os metadados conhecidos fornecem informações descritivas para um item que faz referência a um arquivo. Por exemplo, o valor dos metadados conhecidos chamado `FullPath` é o caminho completo do arquivo referenciado. Para obter mais informações, consulte [Itens](../msbuild/msbuild-items.md).

 multiplataforma A capacidade de um projeto de aplicativo ou de assembly de ser direcionado a vários CLRs e estruturas diferentes do MSBuild e do Visual Studio.

 perfil Um subconjunto da estrutura completa. Ele é usado para minimizar a quantidade que precisa ser baixado para um computador.

 arquivo de projeto Um arquivo de projeto contém o script do MSBuild que controla o build. Normalmente, os arquivos de projeto têm uma extensão de arquivo que termina com *proj*, como *.csproj* ou *.vbproj*. Os arquivos de projeto podem importar arquivos de propriedade e de destino.

 propriedade Uma propriedade é um par chave-valor que é usado para controlar o processo de build. Para obter mais informações, confira [Propriedades do MSBuild](../msbuild/msbuild-properties.md).

 propriedade, ambiente Uma propriedade de ambiente é uma propriedade que é inicializada automaticamente com o valor de uma variável de ambiente do sistema que tem o mesmo nome. Para obter mais informações, confira [Propriedades do MSBuild](../msbuild/msbuild-properties.md).

 arquivo de propriedade Um arquivo de propriedade é um arquivo de projeto que contém principalmente grupos de propriedades e grupos de itens que orientam o build. Por convenção, ele tem a extensão de arquivo *.props*. Normalmente, os arquivos de propriedade são importados no início dos arquivos de projeto associados.

 propriedade, função Uma função de propriedade é uma propriedade do sistema ou um método que pode ser usado para avaliar scripts do MSBuild. Os métodos de propriedade podem ser usados para ler a hora do sistema, comparar cadeias de caracteres, combinar expressões regulares e executar outras ações. Para obter mais informações, confira [Funções de propriedade](../msbuild/property-functions.md).

 função de propriedade, aninhada As funções de propriedade podem ser combinadas para formar funções mais complexas. Por exemplo,

 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`

 Para obter mais informações, confira [Funções de propriedade](../msbuild/property-functions.md).

 propriedade, global Uma propriedade global é um par chave-valor que é usado para controlar o processo de build. As propriedades globais são definidas em um prompt de comando ou usando o atributo `Properties` de uma [tarefa do MSBuild](../msbuild/msbuild-task.md) e não podem ser modificadas durante a fase de avaliação de um build. Para obter mais informações, confira [Propriedades do MSBuild](../msbuild/msbuild-properties.md).

 propriedade, local Uma propriedade local é um par chave-valor que é usado para controlar o processo de build. Este termo é usado apenas para distinguir uma propriedade que não é uma propriedade global.

 propriedade, Registro Uma propriedade de Registro tem um valor que é definido usando uma sintaxe especial que lê o valor de uma subchave de Registro do sistema. Para obter mais informações, confira [Propriedades do MSBuild](../msbuild/msbuild-properties.md).

 propriedade, reservada Uma propriedade reservada é um par chave-valor que é usado para controlar o processo de build. As propriedades reservadas são inicializadas automaticamente com valores predefinidos. Para obter mais informações, confira [Propriedades do MSBuild](../msbuild/msbuild-properties.md).

 escopo do projeto O escopo do projeto descreve um objeto do MSBuild, por exemplo, uma propriedade local, que é visível somente no arquivo de projeto recipiente e nos projetos importados por ele.

 projeto, filho Um projeto filho é criado pela tarefa do MSBuild durante um build de projeto. Esse novo projeto é um filho do projeto que contém ou importa o destino que contém a tarefa do MSBuild. O projeto filho herda as propriedades globais do projeto pai, a menos que elas tenham sido modificadas pelo atributo `Properties`.

 lista de redistribuição Lista de redistribuição: a lista de assemblies que corresponde a determinada estrutura.

 assembly de referência Um assembly que é usado durante o tempo de design para criar um aplicativo. Um assembly de referência pode ter o código real e as interfaces privadas removidos dele, deixando apenas os metadados e as interfaces públicas.

 propriedade de Registro Confira *propriedade, Registro*.

 destino Um destino agrupa tarefas em uma ordem específica e expõe seções do arquivo de projeto como pontos de entrada para o processo de build. Para obter mais informações, consulte [Destinos](../msbuild/msbuild-targets.md).

 destino, criar Confira destino, executar.

 destino, avaliar Devido à compilação incremental, os destinos precisam ser analisados quanto a possíveis alterações nas propriedades e nos itens. Mesmo se o destino for ignorado, essas alterações deverão ser feitas. Avaliar um destino significa executar essa análise e fazer essas alterações. Para obter mais informações, confira [Builds incrementais](../msbuild/incremental-builds.md).

 destino, executar A execução de um destino significa avaliá-lo e executar todas as tarefas que não têm condições ou cujas condições são avaliadas como verdadeiro. Durante a compilação incremental, os destinos podem ser ignorados ou executados, mas eles são sempre avaliados. Para obter mais informações, consulte destino, avaliação.

 destino, executar Um destino que tem uma condição avaliada como falso não é executado, ou seja, não tem nenhum efeito no build. Os destinos em execução são executados ou ignorados. Em ambos os casos, o destino é avaliado. Para obter mais informações, consulte destino, avaliação.

 destino, ignorar Se a compilação incremental determina que todos os arquivos de saída estão atualizados, o destino é ignorado, ou seja, o destino é avaliado, mas as tarefas dentro do destino não são executadas. Para obter mais informações, consulte destino, avaliação.

 moniker da estrutura de destino Um nome que descreve a estrutura (como .NET Framework, Silverlight etc.), a versão e o perfil (como Cliente, Servidor etc.) que você deseja usar como destino.

 pacote de direcionamento A lista de assemblies que são distribuídos com determinada estrutura e o conjunto de assemblies de referência dessa estrutura.

 arquivo de destino Um arquivo de destino é um arquivo de projeto que contém principalmente destinos e tarefas que orientam o build. Por convenção, ele tem a extensão de arquivo *.targets*. Normalmente, os arquivos de destino são importados no fim dos arquivos de projeto associados.

 tarefa As tarefas são unidades de código executável usadas por projetos do [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] para executar operações de build. Por exemplo, uma tarefa pode compilar os arquivos de entrada ou executar uma ferramenta externa. Para obter mais informações, consulte [Tarefas](../msbuild/msbuild-tasks.md).

 transformação Uma transformação é uma conversão individual de uma coleção de itens para outra. Além de habilitar um projeto para converter as coleções de itens, uma transformação permite que um destino identifique um mapeamento direto entre suas entradas e saídas. Para obter mais informações, consulte [Transformações](../msbuild/msbuild-transforms.md).

 metadados conhecidos Confira *metadados, conhecidos*.

## <a name="see-also"></a>Consulte também
- [MSBuild](../msbuild/msbuild.md)