---
title: Recolher e expandir as regiões de código
description: Saiba como você pode usar os comandos expandir e recolher para trabalhar no modo de estrutura de tópicos no Visual Studio
ms.custom: SEO-VS-2020
ms.date: 10/15/2020
ms.topic: conceptual
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 04a2156723bc33e25a658814b9348655f7ba86d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909054"
---
# <a name="outlining"></a>Estrutura de tópicos

Você pode optar por ocultar alguns códigos da exibição recolhendo uma região do código para que ele apareça em um sinal de adição ( **+** ). Você expande uma região recolhida clicando no sinal de adição. Se você for um usuário de teclado, poderá escolher **Ctrl** + **m** + **m** para recolher e expandir. Você também pode recolher uma região de estrutura de tópicos clicando duas vezes em qualquer linha na região na margem da estrutura de tópicos, que aparece à esquerda do código. Você pode ver o conteúdo de uma região recolhida como uma dica de ferramenta quando focaliza a região recolhida.

> [!NOTE]
> Este tópico aplica-se ao Visual Studio no Windows. Para o Visual Studio para Mac, confira [Editor de código-fonte (Visual Studio para Mac)](/visualstudio/mac/source-editor).

As regiões na margem da estrutura de tópicos também são realçadas quando você focaliza a margem com o mouse. A cor de realce padrão pode parecer bastante esmaecida em algumas configurações de cor. Você pode alterá-lo em **ferramentas**  >  **Opções**  >    >  **fontes de ambiente e cores**  >  **recolhíveis região**.

Quando você trabalha no código de estrutura de tópicos, pode expandir as seções nas quais deseja trabalhar, recolhê-las quando terminar e passar para outras seções. Quando você não quiser que a estrutura de tópicos seja exibida, você pode usar o comando **Interromper Estrutura de Tópicos** para remover as informações de estrutura de tópicos sem afetar o código subjacente.

Os comandos **Desfazer** e **Refazer** no menu **Editar** afetam essas ações. As operações de **Copiar**, **Recortar**, **Colar** e do tipo "arrastar e soltar" retêm informações de estrutura de tópico, mas não o estado da região recolhível. Por exemplo, quando você copia uma região recolhida, a operação **Colar** colará o texto copiado como uma região expandida.

> [!CAUTION]
> Quando você altera uma região de estrutura de tópicos, a estrutura de tópicos pode ser perdida. Por exemplo, as exclusões ou as operações de **localização e substituição** podem apagar o final da região.

Os comandos a seguir podem ser encontrados no   >  submenu editar **estrutura de tópicos** .

|Nome|Descrição|
|-|-|
|Ocultar Seleção|(**Ctrl** + **M**, **Ctrl** + **H**) – recolhe um bloco de código selecionado que normalmente não estaria disponível para a estrutura de tópicos, por exemplo, um `if` bloco. Para remover a região personalizada, use **Interromper Ocultação Atual** (ou **Ctrl**+**M**, **Ctrl**+**U**). Não disponível no Visual Basic.|
|Ativar/Desativar Expansão da Estrutura de Tópicos| (**Ctrl** + **M**, **Ctrl** + **m**) – reverte o estado atual oculto ou expandido da seção de estrutura de tópicos mais interna quando o cursor está em uma seção aninhada contraída.|
|Ativar/Desativar Estrutura de Tópicos para Tudo|(**Ctrl** + **M**, **Ctrl** + **L**) – define todas as regiões para o mesmo estado recolhido ou expandido. Se algumas regiões estiverem expandidas e algumas estiverem recolhidas, as regiões recolhidas serão expandidas.|
|Interromper Estrutura de Tópicos|(**Ctrl** + **M**, **Ctrl** + **P**) – remove todas as informações de estrutura de tópicos de todo o documento.|
|Interromper Ocultação Atual|(**Ctrl** + **M**, **Ctrl** + **U**) – remove as informações de estrutura de tópicos para a região definida pelo usuário selecionada no momento. Não disponível no Visual Basic.|
|Recolher para Definições|(**Ctrl** + **M**, **Ctrl** + **o**)-recolhe os membros de todos os tipos.|
|Recolher bloco:\<logical boundary>|C Recolhe uma região na função que contém o ponto de inserção. Por exemplo, se o ponto de inserção estiver dentro de um loop, o loop será ocultado.|
|Recolher tudo em: \<logical structures>|C Recolhe todas as estruturas dentro da função.|

Você também pode usar o SDK do Visual Studio para definir as regiões de texto que deseja expandir ou recolher. Consulte [Instruções passo a passo: estrutura de tópicos](../extensibility/walkthrough-outlining.md).

## <a name="see-also"></a>Confira também

- [Recursos do editor de código](../ide/writing-code-in-the-code-and-text-editor.md)
- [Editor de código-fonte (Visual Studio para Mac)](/visualstudio/mac/source-editor)
