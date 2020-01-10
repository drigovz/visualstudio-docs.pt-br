---
title: Atualizar modelos de item de projeto existentes
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 44f99646330d3c8a75bd94310bc0adf9073f9d49
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591353"
---
# <a name="how-to-update-existing-templates"></a>Como atualizar modelos existentes

Depois de criar um modelo e compactar os arquivos em um arquivo *.zip*, modifique o modelo. É possível fazer isso alterando manualmente os arquivos no modelo ou exportando um novo modelo de um projeto com base no modelo.

## <a name="use-the-export-template-wizard"></a>Use o Assistente para Exportar Modelo

O Visual Studio fornece um **Assistente para Exportar Modelo** que pode ser usado para atualizar um modelo existente.

1. Escolha **Arquivo** > **Novo** > **Projeto** na barra de menus.

1. Selecione o modelo que você deseja atualizar e continue seguindo as etapas para criar o projeto.

1. Modifique o projeto no Visual Studio. Por exemplo, altere o tipo de saída ou adicione um novo arquivo ao projeto.

1. No menu **Projeto**, escolha **Exportar Modelo**.

    O **Assistente para Exportar Modelo** é aberto.

1. Siga os prompts no assistente para exportar o modelo como um arquivo *.zip*.

1. (Opcional) Coloque o arquivo *.zip* no seguinte diretório: *%USERPROFILE%\Documents\Visual Studio\<\>versão\Templates\ProjectTemplates* para disponibilizá-lo para seleção. Você precisará executar essa etapa se você não tiver selecionado a opção **Importar automaticamente o modelo no Visual Studio** no **Assistente para Exportar Modelo**.

1. Exclua o arquivo *.zip* de modelo antigo.

## <a name="manually-update-an-existing-template"></a>Atualizar manualmente um modelo existente

Você pode atualizar um modelo existente sem usar o **Assistente de Exportação de Modelo**, modificando os arquivos no arquivo *.zip* compactado.

### <a name="to-manually-update-an-existing-template"></a>Para atualizar manualmente um modelo existente

1. Localize o arquivo *.zip* que contém o modelo. Os modelos de projeto do usuário estão localizados em *%USERPROFILE%\Documents\Visual Studio \<versão\>\Templates\ProjectTemplates*.

1. Extraia o arquivo *.zip*.

1. Modifique ou exclua os arquivos de modelo atuais ou adicione novos arquivos ao modelo.

1. Abra, modifique e salve o arquivo XML *.vstemplate* para tratar o comportamento atualizado ou novos arquivos.

    Para obter mais informações sobre o esquema *.vstemplate*, consulte [Referência de esquema de modelo do Visual Studio (extensibilidade)](../extensibility/visual-studio-template-schema-reference.md). Para obter mais informações sobre o que você pode parametrizar nos arquivos de origem, consulte [Parâmetros do modelo](../ide/template-parameters.md).

1. Selecione os arquivos em seu modelo, clique no menu de contexto ou no menu acionado com o botão direito do mouse e escolha **Enviar para** > **Pasta compactada (zipada)** .

    Os arquivos selecionados são compactados em um arquivo *.zip*.

1. Coloque o novo arquivo *.zip* no mesmo diretório do antigo arquivo *.zip*.

1. Exclua os arquivos de modelo extraídos e o arquivo *.zip* de modelo antigo.

## <a name="see-also"></a>Veja também

- [Personalizar modelos](../ide/customizing-project-and-item-templates.md)
- [Criar modelos de projeto e de item](../ide/creating-project-and-item-templates.md)
- [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Parâmetros de modelo](../ide/template-parameters.md)
