---
title: Adicionar cabeçalho de arquivo
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 44c3b64d9fb8944a578d054b7d98d4bf39bde3bc
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810370"
---
# <a name="add-file-header"></a>Adicionar cabeçalho de arquivo

Esta geração de código aplica-se a:

- C#

- Visual Basic

**O que:** Adicione cabeçalhos de arquivo a arquivos, projetos e soluções existentes usando um [EditorConfig](../create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

**Quando:** Você deseja adicionar facilmente um cabeçalho de arquivo a arquivos, projetos e soluções.

**Por que:** Sua equipe exige que você inclua um cabeçalho de arquivo para fins de direitos autorais. 

## <a name="how-to"></a>Instruções

1. Adicione um [EditorConfig](../create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project) a um projeto ou solução se você ainda não tiver um.

2. Adicione a seguinte regra ao arquivo EditorConfig: *file_header_template*.

3. Defina o valor da regra como igual ao texto do cabeçalho que você deseja aplicar. Você pode usar `{fileName}` como um espaço reservado para o nome do arquivo.

    ![Regra de cabeçalho do arquivo EditorConfig](media/add-file-header-rule.png)

    > [!NOTE]
    > Você não pode ter multilinhas explícitas em um EditorConfig e precisará usar o caractere de nova linha do UNIX para inserir novas linhas.

4. Coloque o cursor na primeira linha de qualquer arquivo em C# ou Visual Basic.

5. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.

6. Selecione **Adicionar cabeçalho de arquivo**. 

    ![Regra de cabeçalho do arquivo EditorConfig](media/add-file-header.png)

7. Para aplicar o cabeçalho de arquivo a um projeto ou solução inteira, selecione **projeto** ou **solução** na opção **corrigir todas as ocorrências em:** .

8. A caixa de diálogo **corrigir todas as ocorrências** será aberta, onde você poderá visualizar as alterações.

    ![Caixa de diálogo corrigir todas as ocorrências](media/file-header-preview-changes.png)

8. Selecione **aplicar** para aplicar as alterações.

## <a name="see-also"></a>Confira também

- [Geração de código](../code-generation-in-visual-studio.md)
- [Visualizar Alterações](../../ide/preview-changes.md)