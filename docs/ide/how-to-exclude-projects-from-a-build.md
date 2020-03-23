---
title: Como excluir projetos de um build
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a19c49482c45aa0a3cf5d7cb33eb106adb65b83b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114808"
---
# <a name="how-to-exclude-projects-from-a-build"></a>Como excluir projetos de um build

É possível compilar uma solução sem compilar todos os projetos que ela contém. Por exemplo, é possível excluir um projeto que interrompe o build. É possível compilar o projeto depois de investigar e resolver os problemas.

É possível excluir um projeto adotando as seguintes abordagens:

- Removê-lo temporariamente da configuração da solução ativa.

- Criando uma configuração de solução que não inclui o projeto.

Para obter mais informações, consulte [Compreender configurações de build](../ide/understanding-build-configurations.md).

## <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>Para remover temporariamente um projeto da configuração da solução ativa

1. Na barra de menu, escolha **Build** > **Configuration Manager**.

2. Na tabela **Contextos do projeto**, localize o projeto que você deseja excluir do build.

3. Na coluna **Build** do projeto, desmarque a caixa de seleção.

4. Escolha o botão **Fechar** e, em seguida, recompile a solução.

## <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>Para criar uma configuração da solução que exclui um projeto

1. Na barra de menu, escolha **Build** > **Configuration Manager**.

2. Na lista **de configuração da solução Active,** escolha ** \<Nova>**.

3. Na caixa **Nome**, insira um nome para a configuração da solução.

4. Na lista **Copiar configurações de**, escolha a configuração da solução na qual você deseja basear a nova configuração (por exemplo, **Depurar**) e, em seguida, escolha o botão **OK**.

5. Na caixa de diálogo **Configuration Manager**, desmarque a caixa de seleção na coluna **Build** do projeto que você deseja excluir e, em seguida, escolha o botão **Fechar**.

6. Na barra de ferramentas **Padrão**, verifique se a nova configuração da solução é a configuração ativa na caixa **Configurações da Solução**.

7. Na barra de menu, escolha **Build** > **Rebuild Solution**.

## <a name="skipped-projects"></a>Projetos ignorados

Os projetos podem ser ignorados durante a construção porque não estão atualizados ou porque estão excluídos da configuração. O Visual Studio usa o MSBuild para construir seus projetos. O MSBuild só constrói um destino se a saída for mais antiga que a entrada, conforme determinado pelos carimbos de tempo do arquivo. Para forçar uma reconstrução, use o comando **Build** > **Rebuild Solution**.

No painel **Build** da janela **Saída,** o Visual Studio relata o número de projetos que estavam atualizados, o número que construiu com sucesso, o número que falhou e o número que foram ignorados. A contagem ignorada não inclui projetos que não foram construídos por estarem atualizados. Quando os projetos são excluídos da configuração ativa, eles são ignorados durante a compilação. Na saída de compilação, você vê uma mensagem indicando que o projeto está ignorado:

```output
2>------ Skipped Build: Project: ConsoleApp2, Configuration: Debug x86 ------
2>Project not selected to build for this solution configuration
```

Para descobrir por que um projeto foi ignorado, observe a configuração ativa`Debug x86` (no exemplo anterior) e escolha **Build** > Configuration**Manager**. Você pode visualizar ou alterar quais projetos são ignorados para cada configuração, conforme discutido neste artigo.

## <a name="see-also"></a>Confira também

- [Compreender configurações de build](../ide/understanding-build-configurations.md)
- [Como criar e editar configurações](../ide/how-to-create-and-edit-configurations.md)
- [Como: Construir várias configurações simultaneamente](../ide/how-to-build-multiple-configurations-simultaneously.md)
