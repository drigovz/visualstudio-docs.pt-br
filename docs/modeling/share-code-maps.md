---
title: Exportar e salvar mapas de código
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- multiple
ms.openlocfilehash: a4f53f349b4bc2f578ad007761df32e5c4145dbc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54984490"
---
# <a name="share-code-maps"></a>Compartilhar mapas de códigos

Você pode salvar mapas de código como parte de um projeto do Visual Studio, como uma imagem ou como um arquivo XPS.

## <a name="share-a-code-map-with-other-visual-studio-users"></a>Compartilhar um mapa de código com outros usuários do Visual Studio

Use o **arquivo** menu para salvar o mapa.

-ou-

Para salvar o mapa como parte do projeto específico, na barra de ferramentas do mapa, escolha **compartilhamento** > **mover \<CodeMapName >. dgml em**e, em seguida, escolha o projeto onde você deseja salvar o mapa.

![Mover um mapa em outro projeto](../modeling/media/codemapsmovemapmenu.png)

O Visual Studio salva o mapa como uma *dgml* arquivo que você pode compartilhar com outros usuários do Visual Studio Enterprise e Professional do Visual Studio.

> [!NOTE]
> Antes de compartilhar um mapa com aqueles que usam o Visual Studio Professional, certifique-se expandir todos os grupos, Mostrar nós ocultos e links de grupo cruzado e recuperar todos os nós excluídos que você deseja que outras pessoas vejam no seu mapa. Do contrário, outros usuários não poderão consultar esses itens.
>
> O seguinte erro poderá ocorrer quando você salva um mapa que está em um projeto de modelagem ou foi copiado de um projeto de modelagem para outro local:
>
> "Não é possível salvar *fileName* fora do diretório do projeto. Itens vinculados não são compatíveis."
>
> O Visual Studio mostra o erro, mas cria a versão salva de qualquer maneira. Para evitar o erro, crie o mapa fora do projeto de modelagem. Em seguida, é possível salvá-lo no local desejado. Apenas copiar o arquivo para outro local na solução e, em seguida, tentar salvá-lo não funcionará.

## <a name="export-a-code-map-as-an-image"></a>Exportar um mapa de código como uma imagem

Quando você exporta um mapa de código como uma imagem, você pode copiá-lo para outros aplicativos, como Microsoft Word ou PowerPoint.

1. Na barra de ferramentas de mapa de código, escolha **compartilhamento** > **Email como imagem** ou **Copiar imagem**.

2. Cole a imagem em outro aplicativo.

## <a name="export-the-map-as-an-xps-file"></a>Exportar o mapa como um arquivo XPS

Quando você exporta um mapa de código como um arquivo XPS, você poderá ver isso em visualizadores XML ou XAML como o Internet Explorer.

1. Na barra de ferramentas de mapa de código, escolha **compartilhamento** > **Email como XPS portátil** ou **Salvar como XPS portátil**.

2. Navegue para onde você deseja salvar o arquivo.

3. Nome do mapa de código. Certifique-se de que o **Salvar como tipo** caixa é definida como **arquivos XPS (\*. XPS)**. Escolher **salvar**.

## <a name="see-also"></a>Consulte também

- [Mapear dependências com mapas de código](../modeling/map-dependencies-across-your-solutions.md)