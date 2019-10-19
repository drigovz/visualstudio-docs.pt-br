---
title: Como exibir, salvar e configurar arquivos de log de build |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ffc1c620136c55c42f3468129ed164075d762bff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670501"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Como ver, salvar e configurar arquivos de log de build
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Depois de compilar um projeto no Visual Studio IDE, é possível exibir informações sobre sse build na Janela de **Saída**. Usando essas informações, é possível, por exemplo, solucionar problemas de uma falha de build. Para projetos C++, também é possível exibir as mesmas informações em um arquivo .txt criado e salvo automaticamente. Para projetos de código gerenciado, é possível copiar e colar as informações da Janela de **Saída** em uma arquivo .txt e salvá-lo. Também é possível usar o IDE para especificar que tipos de informações você deseja exibir sobre cada build.

 Se você compilar qualquer tipo de projeto usando o MSBuild, é possível criar um arquivo .txt para salvar informações sobre o build. Para obter mais informações, consulte [Obtaining Build Logs (Obtendo logs de build)](../msbuild/obtaining-build-logs-with-msbuild.md).

### <a name="to-view-the-build-log-file-for-a-c-project"></a>Para exibir o arquivo de log de build para um projeto C++

1. No **Windows Explorer** ou no **Explorador de Arquivos**, abra o seguinte arquivo: \\...\Visual Studio *Versão*\Projects\\*ProjectName*\\*ProjectName*\Debug\\*ProjectName*.txt

### <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Para criar um arquivo de log de build para um projeto de código gerenciado

1. Na barra de menus, escolha **Compilar**, **Compilar Solução**.

2. Na Janela de **Saída**, realce as informações do build e, em seguida, copie-as para a área de transferência.

3. Abra um editor de texto, como o Bloco de notas, cole as informações no arquivo e salve-o.

### <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Para alterar a quantidade de informações incluídas no log de build

1. Na barra de menus, escolha **Ferramentas**, **Opções**.

2. Na página **Projetos e Soluções**, escolha a página **Compilar e Executar**.

3. Na lista **Detalhamento da saída de build do projeto no MSBuild**, escolha um dos seguintes valores e, em seguida, escolha o botão **OK**.

    |Nível de detalhes|DESCRIÇÃO|
    |---------------------|-----------------|
    |Silenciosa|Exibe apenas um resumo do build.|
    |Mínimo|Exibe um resumo do build e dos erros, avisos e mensagens categorizadas como altamente importantes.|
    |Normal|Exibe um resumo do build; erros, avisos e mensagens categorizados como altamente importantes; e as principais etapas do build. Use esse nível de detalhes com mais frequência.|
    |Detalhado|Exibe um resumo do build; erros, avisos e mensagens categorizados como altamente importantes; todas as etapas do build; e as mensagens categorizadas com base na importância normal.|
    |Diagnóstico|Exibe todos os dados disponíveis para o build. É possível usar este nível de detalhes para ajudar a depurar problemas com scripts de build personalizados e outros problemas de build.|

     Para obter mais informações, consulte [Caixa de diálogo Opções, Projetos e Soluções, Compilar e Executar](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) e <xref:Microsoft.Build.Framework.LoggerVerbosity>.

    > [!IMPORTANT]
    > É necessário recompilar o projeto para que suas alterações tenham efeito na Janela de **Saída** (todos os projetos) e no arquivo *ProjectName*.txt (apenas projetos C++).

## <a name="see-also"></a>Veja também
 [Obtendo logs de compilação](../msbuild/obtaining-build-logs-with-msbuild.md) [compilando e limpando projetos e soluções no Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md) [compilando e compilando](../ide/compiling-and-building-in-visual-studio.md)
