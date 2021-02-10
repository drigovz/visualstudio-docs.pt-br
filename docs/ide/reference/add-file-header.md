---
title: Adicionar cabeçalho de arquivo
description: Saiba como usar um arquivo EditorConfig para adicionar cabeçalhos de arquivo a arquivos, projetos e soluções existentes.
ms.custom: SEO-VS-2020
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 2b177092b04d5042f62dfd0b34d2bfbf4f1f0228
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933863"
---
# <a name="add-file-header"></a>Adicionar cabeçalho de arquivo

Esta geração de código aplica-se a:

- C#

- Visual Basic

**O que:** Adicione cabeçalhos de arquivo a arquivos, projetos e soluções existentes usando um [EditorConfig](../create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

**Quando:** Você deseja adicionar facilmente um cabeçalho de arquivo a arquivos, projetos e soluções.

**Por que:** Sua equipe exige que você inclua um cabeçalho de arquivo para fins de direitos autorais. 

## <a name="how-to"></a>Como fazer

1. Adicione um [EditorConfig](../create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project) a um projeto ou solução se você ainda não tiver um.

2. Adicione a seguinte regra ao arquivo EditorConfig: *file_header_template*.

3. Defina o valor da regra como igual ao texto do cabeçalho que você deseja aplicar. Você pode usar `{fileName}` como um espaço reservado para o nome do arquivo.

    ![Captura de tela do arquivo EditorConfig mostrando o valor de file_header_template.](media/add-file-header-rule.png)

    > [!NOTE]
    > Você não pode ter multilinhas explícitas em um EditorConfig e precisará usar o caractere de nova linha do UNIX para inserir novas linhas.

4. Coloque o cursor na primeira linha de qualquer arquivo em C# ou Visual Basic.

5. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.

6. Selecione **Adicionar cabeçalho de arquivo**. 

    ![Captura de tela da opção Adicionar cabeçalho de arquivo.](media/add-file-header.png)

7. Para aplicar o cabeçalho de arquivo a um projeto ou solução inteira, selecione **projeto** ou **solução** na opção **corrigir todas as ocorrências em:** .

8. A caixa de diálogo **corrigir todas as ocorrências** será aberta, onde você poderá visualizar as alterações.

    ![Caixa de diálogo corrigir todas as ocorrências](media/file-header-preview-changes.png)

8. Selecione **aplicar** para aplicar as alterações.

## <a name="see-also"></a>Confira também

- [Geração de código](../code-generation-in-visual-studio.md)
- [Visualizar Alterações](../../ide/preview-changes.md)