---
title: Ler modelos e diagramas em outras edições do Visual Studio
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- models, versions of Visual Studio
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29c190115836972f86590233e331f172422efbd6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747431"
---
# <a name="read-models-and-diagrams-in-other-visual-studio-editions"></a>Ler modelos e diagramas em outras edições do Visual Studio

Quando você abre um modelo em uma versão do Visual Studio que não dá suporte à criação de modelo, o modelo é aberto no modo somente leitura. Nesse modo, você pode alterar o layout dos diagramas, mas não pode alterar o modelo.

Para ver quais versões do Visual Studio oferecem suporte à criação de modelo, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="obtaining-access-to-a-model-and-diagrams"></a>Obtendo acesso a um modelo e diagramas

Para ler um diagrama de dependência, você deve primeiro usar o Visual Studio para abrir o projeto de modelagem e, em seguida, abrir o diagrama dentro dele.

Por esse motivo, se você quiser ler um diagrama de dependência, também deverá ter acesso ao projeto de modelagem no qual ele foi criado. Você pode fazer isso acessando o projeto do controle do código-fonte ou obtendo uma cópia dos arquivos do projeto.

> [!NOTE]
> Isso não se aplica a mapas de código e diagramas de classe .NET gerados a partir do código. Esses diagramas podem ser exibidos independentemente de um projeto de modelagem.

Para ler um diagrama de dependência, o conjunto mínimo de arquivos de que você precisa é o seguinte:

- Os dois arquivos de diagrama do diagrama que você deseja ler, por exemplo, **MyDiagram. classdiagram e MyDiagram. classdiagram. layout**.

    > [!NOTE]
    > Para diagramas de dependência, você também deve ter o arquivo chamado _MyDiagram_ **. layerdiagram. supressões**.

- O arquivo de projeto de modelagem (**MyModel. modelproj**)

- O arquivo de modelo raiz (**ModelDefinition\MyModel.Uml**)

- Os arquivos de pacote para qualquer pacote referenciado no diagrama (**ModelDefinition\MyPackage.Uml**)

## <a name="changes-that-you-can-make-in-read-only-mode"></a>Alterações que você pode fazer no modo somente leitura

Se você abrir um modelo e seus diagramas em uma versão do Visual Studio que não ofereça suporte à criação de modelo, não será possível alterar o modelo. Ou seja, você não pode alterar os elementos e as relações que são exibidos nos diagramas ou no Gerenciador de modelos. No entanto, você pode fazer algumas alterações no layout dos diagramas:

- Reorganize as formas e os conectores no diagrama.

- Expandir e recolher formas.

Você pode salvar essas alterações. Se você quiser tornar as alterações visíveis para outros usuários, será necessário pelo menos enviar os arquivos **. layout** atualizados.

## <a name="see-also"></a>Consulte também

- [Diagramas de dependência: referência](../modeling/layer-diagrams-reference.md)
- [Criar modelos para o aplicativo](../modeling/create-models-for-your-app.md)