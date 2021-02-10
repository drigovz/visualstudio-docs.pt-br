---
title: Modelos de projetos e arquivos
description: Saiba mais sobre como os modelos de projeto e item fornecem stubs reutilizáveis que dão a usuários algum código e estrutura básicos.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], project
- templates [Visual Studio], item
- item templates [Visual Studio]
- project templates [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: e5a3a555a9c0674c70e93ec557416c05d282fbcf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956809"
---
# <a name="project-and-item-templates"></a>Modelos de projeto e de item

Os modelos de projeto e de item fornecem stubs reutilizáveis que oferecem aos usuários uma estrutura e um código básico que eles podem personalizar para suas próprias finalidades.

## <a name="visual-studio-templates"></a>modelos do Visual Studio

Vários modelos de itens e de projetos predefinidos são instalados com o Visual Studio. É possível escolher entre esses modelos, tais como os modelos **Aplicativo Web ASP.NET** e **Biblioteca de Classes**, quando você cria um projeto. Os modelos de item, tais como arquivos de código, arquivos XML, páginas HTML e folhas de estilo, aparecem na janela **Adicionar Novo Item**.

Esses modelos fornecem um ponto de partida para os usuários começarem a criar projetos ou expandir projetos existentes. Os modelos de projeto fornecem os arquivos que são necessários para um tipo de projeto específico, incluem referências de assembly padrão e definem opções de compilador e propriedades de projeto padrão. Os modelos de item podem variar em complexidade desde apenas um arquivo vazio com uma determinada extensão de arquivo até vários arquivos de código-fonte com código de stub, arquivos de informações de designer e recursos inseridos.

Você pode usar modelos instalados, criar seus próprios modelos personalizados ou baixar e usar modelos criados pela comunidade. Para obter mais informações, consulte [Como criar modelos de projeto](../ide/how-to-create-project-templates.md) e [Como criar modelos de item](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Conteúdo de um modelo

Todos os modelos de projeto e de item, sejam eles instalados com o Visual Studio ou criados por você, funcionam usando os mesmos princípios e têm conteúdo semelhante. Todos os modelos contêm os seguintes itens:

- Os arquivos a serem criados quando o modelo é usado. Eles incluem arquivos de código-fonte, recursos inseridos, arquivos de projeto e assim por diante.

::: moniker range="vs-2017"

- Um arquivo *.vstemplate*, contendo os metadados necessários para criar um projeto ou item do modelo e para exibir o modelo nas janelas **Novo Projeto** e **Adicionar Novo Item**.

::: moniker-end

::: moniker range=">=vs-2019"

- Um arquivo *.vstemplate*, contendo os metadados necessários para criar um projeto ou item do modelo e para exibir o modelo na página **Criar um novo projeto** e ou na caixa de diálogo **Adicionar Novo Item**.

::: moniker-end

   Para obter mais informações sobre arquivos *.vstemplate*, confira [Marcas de modelo](template-tags.md) e [Parâmetros de modelo](../ide/template-parameters.md).

Quando esses arquivos são compactados em um arquivo *.zip* e colocados na pasta correta, o Visual Studio os exibe automaticamente nos seguintes locais:

::: moniker range="vs-2017"

- Os modelos de projeto aparecem na janela **Novo Projeto**.

::: moniker-end

::: moniker range=">=vs-2019"

- Os modelos de projeto aparecem na página **Criar um novo projeto**.

::: moniker-end

- Os modelos de item aparecem na janela **Adicionar Novo Item**.

Para obter mais informações sobre pastas de modelo, consulte [Como localizar e organizar modelos](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Consulte também

- [Como: criar modelos de projeto](../ide/how-to-create-project-templates.md)
- [Como: criar modelos de item](../ide/how-to-create-item-templates.md)
- [Marcas de modelo](template-tags.md)
- [Parâmetros de modelo](../ide/template-parameters.md)
- [Personalizar modelos](../ide/customizing-project-and-item-templates.md)
- [Pacotes NuGet em modelos do Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
