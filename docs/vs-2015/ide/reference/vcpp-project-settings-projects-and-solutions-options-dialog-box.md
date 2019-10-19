---
title: Caixa de diálogo Configurações do Projeto VC++, Projetos e Soluções, Opções | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.VCBuild
helpviewer_keywords:
- builds [Visual Studio], logs
- build process [C++]
- files [Visual Studio], built by C/C++ compiler
- file extensions, built by C or C++ compiler
- cl.exe compiler, file extensions
- extensions, files built by C or C++ compiler
- BuildLog.htm
ms.assetid: 56420efd-6a95-464e-b890-e2b38c48d66a
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ef861d13387c013659e5e4c1714680b71896858c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657861"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>Caixa de diálogo Configurações do Projeto do VC++, Projetos e Soluções, Opções
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Esta caixa de diálogo permite que você defina configurações de projeto [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] relacionadas ao log de build e tipos de arquivo de suporte.

### <a name="to-access-this-dialog-box"></a>Para acessar essa caixa de diálogo

1. No menu **Ferramentas**, clique em **Opções**.

2. Selecione **Projetos e Soluções** e, em seguida, selecione **Configurações do Projeto VC++** .

## <a name="build-customization-search-path"></a>Caminho de pesquisa de personalização do build
 Especifica a lista de diretórios que contêm arquivos de .rules, que o ajudarão a definir regras de build para seus projetos.

## <a name="build-logging"></a>Log de build
 **Sim** Ativa a geração do arquivo de log de compilação. Essa opção gera o BuildLog.htm, que pode ser encontrado no diretório de arquivos intermediários do projeto. Cada novo build substitui o arquivo BuildLog.htm anterior.

 **Não** Desativa a geração do arquivo de log de compilação.

## <a name="build-timing"></a>Tempo de build
 **Sim** Ativa o tempo de compilação. Se selecionado, o tempo necessário para a conclusão do build é publicado na Janela de Saída. Para obter mais informações, consulte [Janela de Saída](../../ide/reference/output-window.md).

 **Não** Desativa o tempo de compilação.

## <a name="extensions-to-hide"></a>Extensões a serem ocultadas
 Especifica as extensões de nome de arquivo dos arquivos que não serão exibidos no **Gerenciador de Soluções** quando **Mostrar Todos os Arquivos** for habilitado.

## <a name="extensions-to-include"></a>Extensões a serem incluídas
 Especifica as extensões de nome de arquivo dos arquivos que podem ser portados em seu projeto.

## <a name="maximum-concurrent-c-compilations"></a>Máximo de compilações simultâneas C++
 Especifica o número máximo de núcleos de CPU a serem usados para a compilação C++ paralela.

## <a name="show-environment-in-log"></a>Mostrar ambiente em log
 **Sim** Lista as variáveis de ambiente no arquivo de log de compilação. Essa opção específica o eco para todas as variáveis de ambiente, durante os builds dos projetos [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)], para o arquivo de log de build.

 **Não** Exclua as variáveis de ambiente do arquivo de log de compilação.

## <a name="solution-explorer-mode"></a>Modo do Gerenciador de Soluções
 **Mostrar somente arquivos no projeto** Configura **Gerenciador de soluções** para exibir somente os arquivos no projeto.

 **Mostrar todos os arquivos** Configura **Gerenciador de soluções** para mostrar os arquivos no projeto e os arquivos no disco na pasta do projeto.

## <a name="see-also"></a>Veja também
 [CriandoC++ ](https://msdn.microsoft.com/library/fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008) referência c/programas [cC++ /Build](https://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d)
