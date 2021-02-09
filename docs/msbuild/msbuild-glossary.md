---
title: Glossário do MSBuild
description: Conheça os termos do glossário do Microsoft Build Engine (MSBuild) que descrevem o mecanismo de compilação e seus componentes.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f767d8e4-24d8-4803-80eb-e857202dbe2c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e6e5ef85ffc4a10719cfbef79cbaf6dad08bdbf0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919127"
---
# <a name="msbuild-glossary"></a>Glossário do MSBuild

Esses termos são usados para descrever o MSBuild (Microsoft Build Engine) e seus componentes.

## <a name="assemblyfoldersex"></a>AssemblyFoldersEx

Um local de Registro em que os fornecedores de terceiros armazenam caminhos para cada versão da estrutura que dão suporte ao local em que a resolução do tempo de design pode consultar para localizar assemblies de referência.

## <a name="batching"></a>lote

O envio em lote significa dividir itens em categorias diferentes, conhecidas como *lotes*, com base nos metadados do item e, em seguida, executar um destino ou uma tarefa por vez usando cada lote. O envio em lote é o equivalente do MSBuild para o constructo --loop. Para obter mais informações, consulte [Envio em lote](../msbuild/msbuild-batching.md).

## <a name="build-scope"></a>Escopo de build

O escopo de build descreve um objeto do MSBuild, por exemplo, uma propriedade global, que é potencialmente visível para um projeto e quaisquer projetos filho que são criados em um build de vários projetos.

## <a name="child-project"></a>Projeto filho

Consulte *projeto, filho*.

## <a name="condition"></a>condition

Muitos elementos do MSBuild podem ser definidos condicionalmente; ou seja, o atributo `Condition` aparece no elemento. O conteúdo dos elementos condicionais é ignorado a menos que a condição seja avaliada como `true`. Para obter mais informações, consulte [Condições](../msbuild/msbuild-conditions.md).

## <a name="definition-item"></a>definição, item

Consulte *definição de item*.

## <a name="emit-item"></a>Emissão de item

Durante a fase de execução de um build, os itens podem ser criados ou modificados por tarefas que têm elementos `Output` filho que têm o atributo `ItemName`. Diz-se que a tarefa "emite" os novos itens.

## <a name="emit-property"></a>Emissão de propriedade

Durante a fase de execução de um build, as propriedades podem ser criadas ou modificadas por tarefas que têm elementos `Output` filho que têm o atributo `PropertyName`. Diz-se que a tarefa "emite" a nova propriedade.

## <a name="evaluation-phase"></a>Fase de avaliação

A avaliação é a primeira fase de um build de projeto. Todas as propriedades e os itens são avaliados na ordem em que aparecem no projeto. Os projetos importados são avaliados conforme são encontrados no projeto. Destinos e tarefas não serão executados até a fase de execução e quaisquer propriedades ou itens que eles declarariam ou emitiriam serão ignorados durante a avaliação.

## <a name="execution-phase"></a>Fase de execução

A execução é a segunda fase de um build de projeto. Os destinos selecionados são criados e as tarefas são executadas. As propriedades e os itens podem ser criados ou modificados em comparação com seus valores de avaliação.

## <a name="function-property"></a>função, propriedade

Consulte *função de propriedade*.

## <a name="function-item"></a>função, item

Consulte a função de item.

## <a name="item"></a>item

Os itens são entradas no sistema de build e são agrupados em tipos de item com base em seus nomes de elemento. Normalmente, os itens representam arquivos. Como os itens são nomeados pelo tipo de item ao qual pertencem, os termos *item* e *valor de item* podem ser usados alternadamente. Para obter mais informações, consulte [Itens](../msbuild/msbuild-items.md).

## <a name="item-definition"></a>Definição de item

Os grupos de definição de item contêm as definições de item que adicionam metadados padrão a qualquer tipo de item. Como metadados conhecidos, os metadados padrão estão associados a todos os itens do tipo de item especificado. Os metadados padrão podem ser substituídos explicitamente em uma definição de item. Para obter mais informações, confira [Definições de item](../msbuild/item-definitions.md).

## <a name="item-function"></a>Função de item

As funções de item obtêm informações sobre os itens no projeto. Essas funções simplificam a obtenção de itens Distinct() e são mais rápidas do que executar loop nos itens. Há funções para manipular cadeias de caracteres e caminhos de item. Para saber mais, confira [Funções de item](../msbuild/item-functions.md).

## <a name="item-metadata"></a>metadados de item

Consulte *metadados, item*.

## <a name="item-type"></a>Tipo de item

Os tipos de item são listas nomeadas de itens que podem ser usados como parâmetros para tarefas. As tarefas usam os valores do item para executar as etapas do processo de build. Para obter mais informações, consulte [Itens](../msbuild/msbuild-items.md).

## <a name="metadata-item"></a>metadados, item

Os metadados de item são uma coleção de pares nome-valor associados a um item. Os metadados fornecem informações descritivas para o item e são opcionais, com exceção de metadados bem conhecidos. Para obter mais informações, consulte [Itens](../msbuild/msbuild-items.md).

## <a name="metadata-well-known"></a>metadados, conhecidos

Os metadados conhecidos são metadados de item somente leitura que são inicializados usando um valor predefinido. Os metadados conhecidos fornecem informações descritivas para um item que faz referência a um arquivo. Por exemplo, o valor dos metadados conhecidos chamado `FullPath` é o caminho completo do arquivo referenciado. Para obter mais informações, consulte [Itens](../msbuild/msbuild-items.md).

## <a name="multitargeting"></a>multiplataforma

A capacidade de um projeto de aplicativo ou de assembly de direcionar vários CLRs e estruturas diferentes do MSBuild e do Visual Studio.

## <a name="profile"></a>perfil

Um subconjunto da estrutura completa. Ele é usado para minimizar a quantidade que precisa ser baixado para um computador.

## <a name="project-file"></a>arquivo de projeto

Um arquivo de projeto contém o script MSBuild que controla o build. Normalmente, os arquivos de projeto têm uma extensão de arquivo que termina com *proj*, como *.csproj* ou *.vbproj*. Os arquivos de projeto podem importar arquivos de propriedade e de destino.

## <a name="property"></a>propriedade

Uma propriedade é um par chave-valor que é usado para controlar o processo de build. Para obter mais informações, confira [Propriedades do MSBuild](../msbuild/msbuild-properties.md).

## <a name="property-environment"></a>propriedade, ambiente

Uma propriedade de ambiente é uma propriedade que é inicializada automaticamente para o valor de uma variável de ambiente do sistema que tem o mesmo nome. Para obter mais informações, confira [Propriedades do MSBuild](../msbuild/msbuild-properties.md).

## <a name="property-file"></a>Arquivo de propriedade

Um arquivo de propriedade é um arquivo de projeto que contém principalmente grupos de propriedade e grupos de itens que orientam o build. Por convenção, ele tem a extensão de arquivo *.props*. Normalmente, os arquivos de propriedade são importados no início dos arquivos de projeto associados.

## <a name="property-function"></a>propriedade, função

Uma função de propriedade é uma propriedade do sistema ou um método que pode ser usado para avaliar scripts do MSBuild. Os métodos de propriedade podem ser usados para ler a hora do sistema, comparar cadeias de caracteres, combinar expressões regulares e executar outras ações. Para obter mais informações, confira [Funções de propriedade](../msbuild/property-functions.md).

## <a name="property-function-nested"></a>função de propriedade, aninhada

As funções de propriedade podem ser combinadas para formar funções mais complexas. Por exemplo,

 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`

Para obter mais informações, confira [Funções de propriedade](../msbuild/property-functions.md).

## <a name="property-global"></a>propriedade, global

Uma propriedade global é um par chave-valor que é usado para controlar o processo de build. As propriedades globais são definidas em um prompt de comando ou usando o atributo `Properties` de uma [tarefa do MSBuild](../msbuild/msbuild-task.md) e não podem ser modificadas durante a fase de avaliação de um build. Para obter mais informações, confira [Propriedades do MSBuild](../msbuild/msbuild-properties.md).

## <a name="property-local"></a>propriedade, local

Uma propriedade local é um par chave-valor que é usado para controlar o processo de build. Este termo é usado apenas para distinguir uma propriedade que não é uma propriedade global.

## <a name="property-registry"></a>propriedade, Registro

Uma propriedade de Registro tem um valor que é definido usando uma sintaxe especial que lê o valor de uma subchave de Registro do sistema. Para obter mais informações, confira [Propriedades do MSBuild](../msbuild/msbuild-properties.md).

## <a name="property-reserved"></a>propriedade, reservada

Uma propriedade reservada é um par chave-valor que é usado para controlar o processo de build. As propriedades reservadas são inicializadas automaticamente com valores predefinidos. Para obter mais informações, confira [Propriedades do MSBuild](../msbuild/msbuild-properties.md).

## <a name="project-scope"></a>Escopo do projeto

O escopo do projeto descreve um objeto do MSBuild, por exemplo, uma propriedade local, que é visível somente no arquivo de projeto e em todos os projetos que ele importa.

## <a name="project-child"></a>projeto, filho

Um projeto filho é criado pela tarefa do MSBuild durante o build do projeto. Esse novo projeto é um filho do projeto que contém ou importa o destino que contém a tarefa do MSBuild. O projeto filho herda as propriedades globais do projeto pai, a menos que elas tenham sido modificadas pelo atributo `Properties`.

## <a name="redist-list"></a>Lista redist

Lista de redistribuição: a lista de assemblies que corresponde a uma determinada estrutura.

## <a name="reference-assembly"></a>Assembly de referência

Um assembly que é usado durante o tempo de design para criar um aplicativo. Um assembly de referência pode ter o código real e as interfaces privadas removidos dele, deixando apenas os metadados e as interfaces públicas.

## <a name="registry-property"></a>Propriedade de Registro

Consulte *propriedade, Registro*.

## <a name="target"></a>destino

Um destino agrupa tarefas em uma ordem específica e expõe seções do arquivo de projeto como pontos de entrada para o processo de build. Para obter mais informações, consulte [Destinos](../msbuild/msbuild-targets.md).

## <a name="target-building"></a>destino, build

Consulte destino, execução.

## <a name="target-evaluating"></a>destino, avaliação

Devido à compilação incremental, os destinos devem ser analisados quanto a possíveis alterações nas propriedades e nos itens. Mesmo se o destino for ignorado, essas alterações deverão ser feitas. Avaliar um destino significa executar essa análise e fazer essas alterações. Para obter mais informações, consulte [Builds incrementais](../msbuild/incremental-builds.md).

## <a name="target-executing"></a>destino, executando

Executar um destino significa avaliá-lo e executar todas as tarefas que não têm condições ou cujas condições são avaliadas como true. Durante a compilação incremental, os destinos podem ser ignorados ou executados, mas eles são sempre avaliados. Para obter mais informações, consulte destino, avaliação.

## <a name="target-running"></a>destino, execução

Um destino que tem uma condição avaliada como false não é executado, ou seja, não tem nenhum efeito no build. Os destinos em execução são executados ou ignorados. Em ambos os casos, o destino é avaliado. Para obter mais informações, consulte destino, avaliação.

## <a name="target-skipping"></a>destino, ignorando

Se a compilação incremental determina que todos os arquivos de saída estão atualizados, então o destino é ignorado, isto é, o destino é avaliado, mas as tarefas dentro do destino não são executadas. Para obter mais informações, consulte destino, avaliação.

## <a name="target-framework-moniker"></a>Moniker de estrutura de destino

Um nome que descreve a estrutura (como .NET Framework, Silverlight etc.), a versão e o perfil (como Cliente, Servidor etc.) que você deseja usar como destino.

## <a name="targeting-pack"></a>Direcionamento de pacote

A lista de assemblies que são distribuídos com uma determinada estrutura e o conjunto de assemblies de referência para essa estrutura.

## <a name="targets-file"></a>Arquivo de destino

Um arquivo de destino é um arquivo de projeto que contém, em grande parte, destinos e tarefas que orientam o build. Por convenção, ele tem a extensão de arquivo *.targets*. Normalmente, os arquivos de destino são importados no fim dos arquivos de projeto associados.

## <a name="task"></a>task

Tarefas são unidades de código executável que os projetos do MSBuild usam para executar operações de compilação. Por exemplo, uma tarefa pode compilar os arquivos de entrada ou executar uma ferramenta externa. Para obter mais informações, consulte [Tarefas](../msbuild/msbuild-tasks.md).

## <a name="transform"></a>transformação

Uma transformação é uma conversão individual de uma coleção de item para outra. Além de habilitar um projeto para converter as coleções de itens, uma transformação permite que um destino identifique um mapeamento direto entre suas entradas e saídas. Para obter mais informações, consulte [Transformações](../msbuild/msbuild-transforms.md).

## <a name="well-known-metadata"></a>metadados conhecidos

Consulte *metadados, conhecidos*.

## <a name="see-also"></a>Confira também

- [MSBuild](../msbuild/msbuild.md)
