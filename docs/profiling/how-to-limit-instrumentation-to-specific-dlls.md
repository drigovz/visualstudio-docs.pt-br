---
title: Como limitar a instrumentação a DLLs específicas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, runtime profiling control window
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 066262a3fae35e82904b011165813e9dd75d9987
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778811"
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>Como limitar a instrumentação a DLLs específicas

Ao usar o método de criação de perfil de instrumentação, é possível limitar a coleta de dados de criação de perfil a uma ou mais DLLs em um aplicativo. Para fazer o perfil de um ou mais DLLs em um aplicativo, crie uma sessão de desempenho que inclua o . *dll* arquivos como alvos. É possível especificar as DLLs que você deseja analisar como projetos em uma solução do Visual Studio ou como arquivos binários independentes.

## <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>Para limitar a instrumentação a DLLs específicas em uma solução do Visual Studio

1. Abra a solução que contém a DLL no Visual Studio.

2. No menu **Analisar**, selecione **Iniciar o Assistente de Desempenho**.

3. Escolha **Instrumentação** como o método de criação de perfil e, em seguida, clique em **Avançar**.

4. A partir **dos seguintes alvos disponíveis você gostaria de perfilar?**, selecione o nome do . *projeto dll* e, em seguida, clique **em Next**.

5. Clique em **Concluir** para sair do assistente e exibir a nova sessão de desempenho na janela **Gerenciador de Desempenho**.

6. Clique com botão direito do mouse em **Destinos** e, em seguida, selecione **Adicionar Projeto de Destino**.

7. Na lista **Adicionar Projeto de Destino**, selecione o projeto executável que você deseja usar para exercer a DLL.

     Opcional. Você pode adicionar todos os projetos DLL que desejar analisar.

8. Para evitar a coleta de dados de um projeto adicionado, clique com o botão direito do mouse no nome do projeto e desmarque a caixa de seleção **Instrumento**.

## <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>Para determinar DLLs específicas a serem analisadas como binários independentes

1. Abra o Visual Studio.

2. No menu **Analisar**, selecione **Iniciar o Assistente de Desempenho**.

3. Em **Para quais dos seguintes destinos disponíveis você deseja criar o perfil?**, selecione **Criar o perfil de uma biblioteca de vínculo dinâmico (.DLL)** e, em seguida, clique em **Avançar**.

4. Na segunda página do assistente, realize as seguintes etapas:

    - Digite o caminho e o nome do arquivo do . *dll* arquivo que você deseja perfilar no **caminho Dll**. Você também pode clicar no botão de reticências (...) para localizar o arquivo na caixa de diálogo **Biblioteca de Vínculo Dinâmico cujo perfil deve ser criado**. Observe que você deve especificar a cópia do . *dll* arquivo que será lançado pelo executável (.* exe*) arquivo que você selecionar a seguir.

    - Digite o caminho e o nome do arquivo do executável (.* exe*) arquivo que vai exercitar o . *dll* em **caminho executável**. Você também pode clicar no botão de reticências (...) para localizar o arquivo na caixa de diálogo **Executável a Ser Iniciado**.

    - Opcional. Digite todos argumentos de linha de comando que você deseja passar para o arquivo executável em **Argumentos de Linha de Comando**. Se necessário, especifique o diretório de trabalho para o aplicativo em **Diretório de trabalho**.

    - Clique em **Avançar**.

5. Escolha **Instrumentação** como o método de criação de perfil e, em seguida, clique em **Avançar**.

6. Clique em **Concluir** para sair do assistente e exibir a nova sessão de desempenho na janela **Gerenciador de Desempenho**.

7. Opcional. Para adicionar mais . *arquivos dll,* clique com o botão direito do mouse **Em Alvos** e, em seguida, **selecione Adicionar binário de destino**. Selecione os arquivos na caixa de diálogo **Adicionar Binário de Destino**.

    > [!NOTE]
    > Não especifique o executável (.* exe*) arquivo que exerce os DLLs.

## <a name="see-also"></a>Confira também

[Controle a coleta de](../profiling/controlling-data-collection.md)
dados[Como: Limitar a instrumentação a funções específicas](../profiling/how-to-limit-instrumentation-to-specific-functions.md)
