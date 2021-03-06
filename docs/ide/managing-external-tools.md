---
title: Gerenciar ferramentas externas
description: Saiba como adicionar e gerenciar novas ferramentas externas que você pode acessar por meio do menu ferramentas.
ms.custom: SEO-VS-2020
ms.date: 11/20/2017
ms.topic: conceptual
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- external tools [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c20c59c720818f3b039e9b0f404a722404cd5669
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903916"
---
# <a name="manage-external-tools"></a>Gerenciar ferramentas externas

Você pode chamar ferramentas externas de dentro do Visual Studio usando o menu **Ferramentas**. Algumas ferramentas padrão estão disponíveis no menu **Ferramentas**, e você pode personalizar o menu adicionando outros executáveis de sua preferência.

## <a name="tools-available-on-the-tools-menu"></a>Ferramentas disponíveis no menu Ferramentas

O menu **Ferramentas** contém vários comandos internos, incluindo:

::: moniker range="vs-2017"

* **Extensões e atualizações** para [Gerenciar extensões do Visual Studio](finding-and-using-visual-studio-extensions.md)
* **Gerenciador de snippets de código** para [Organizar snippets de código](code-snippets.md)
* **Personalizar** para [Personalizar menus e barras de ferramentas](how-to-customize-menus-and-toolbars-in-visual-studio.md)
* **Opções** para [Definir várias opções diferentes para o IDE do Visual Studio e outras ferramentas](reference/options-dialog-box-visual-studio.md)

::: moniker-end

::: moniker range=">=vs-2019"

* **Gerenciador de snippets de código** para [Organizar snippets de código](code-snippets.md)
* **Personalizar** para [Personalizar menus e barras de ferramentas](how-to-customize-menus-and-toolbars-in-visual-studio.md)
* **Opções** para [Definir várias opções diferentes para o IDE do Visual Studio e outras ferramentas](reference/options-dialog-box-visual-studio.md)

::: moniker-end

## <a name="add-new-tools-to-the-tools-menu"></a>Adicionar novas ferramentas ao menu Ferramentas

É possível adicionar uma ferramenta externa para aparecer no menu **Ferramentas**.

1. Abra a caixa de diálogo **Ferramentas externas** escolhendo **ferramentas**  >  **externas ferramentas**.

1. Clique em **Adicionar** e preencha as informações. Por exemplo, a seguinte entrada faz com que o **Windows Explorer** Abra no diretório do arquivo que você abriu atualmente no Visual Studio:

   * Título: `Open File Location`

   * Comando: `explorer.exe`

   * Argumentos: `/root, "$(ItemDir)"`

   ![Caixa de diálogo Ferramentas Externas](media/external-tools-dialog.png)

Esta é uma lista completa de argumentos que podem ser usados ao definir uma ferramenta externa:

|Nome|Argumento|Descrição|
|----------|--------------|-----------------|
|Caminho de item|$(ItemPath)|O nome de arquivo completo do arquivo atual (unidade + caminho + nome de arquivo).|
|Diretório do item|$(ItemDir)|O diretório do arquivo atual (unidade + caminho).|
|Nome de arquivo de item|$(ItemFilename)|O nome de arquivo do arquivo atual (nome de arquivo).|
|Extensão de item|$(ItemExt)|A extensão de nome de arquivo do arquivo atual.|
|Linha atual|$(CurLine)|A posição da linha atual do cursor na janela de código.|
|Coluna atual|$(CurCol)|A posição da coluna atual do cursor na janela de código.|
|Texto atual|$(CurText)|O texto selecionado.|
|Caminho de destino|$(TargetPath)|O nome de arquivo completo do item a ser criado (unidade + caminho + nome de arquivo).|
|Diretório de destino|$(TargetDir)|O diretório do item a ser criado.|
|Nome de destino|$(TargetName)|O nome de arquivo do item a ser criado.|
|Extensão de destino|$(TargetExt)|A extensão de nome de arquivo do item a ser criada.|
|Diretório binário|$(BinDir)|O local final do binário que está sendo criado (definido como unidade + caminho).|
|Diretório do projeto|$(ProjectDir)|O diretório do projeto atual (unidade + caminho).|
|Nome de arquivo do projeto|$(ProjectFileName)|O nome de arquivo do projeto atual (unidade + caminho + nome de arquivo).|
|Diretório da solução|$(SolutionDir)|O diretório da solução atual (unidade + caminho).|
|Nome de arquivo da solução|$(SolutionFileName)|O nome de arquivo da solução atual (unidade + caminho + nome de arquivo).|

> [!NOTE]
> A barra de status do IDE exibe a **linha atual** e as variáveis da **coluna atual** para indicar onde o ponto de inserção está localizado no **Editor de código** ativo. A variável de **texto atual** retorna o texto ou o código selecionado nesse local.

## <a name="see-also"></a>Consulte também

- [Ferramentas de Build do C/C++](/cpp/build/reference/c-cpp-build-tools)
