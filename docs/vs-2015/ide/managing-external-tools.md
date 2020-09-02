---
title: Gerenciar ferramentas externas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- Create GUID tool
- RC (Resource Compiler)
- ReBase tool
- Windows NT Message Compiler
- Windows NT C++ Symbol Undecorator
- tstcon32.exe
- Type Library Generator
- Windows NT Image Binder
- tools [Visual Studio], external
- RowsetViewer tool
- utilities, external tools
- Local Test Manager
- OLE DB Rowset Viewer
- Midlc (IDL Compiler)
- ATL Trace Tool
- Odbcte32w.exe
- IDL Compiler
- HCW (Help Workshop)
- Message Compiler [Visual Studio]
- UUID Generator
- MIDL, external tools
- ErrLook tool
- MAKEHM tool
- Error lookup tool
- OLEVIEW (Object Viewer)
- Uuidgen.exe
- WebDbg tool
- OLE/COM Object Viewer
- LTM (Local Test Manager)
- ATLTraceTool.exe
- Bind tool
- Vsvars32.bat
- external tools [Visual Studio]
- ODBC Test
- Windows NT Image Rebaser
- undname.exe
- Vcspawn.exe
- ActiveX Control Test Container
- mc (Message Compiler)
- GUIDGEN tool
- Odbcte32.exe
- DisableMsg tool
- MkTypLib tool
- Help Workshop
- Resource Compiler
ms.assetid: f382fd40-a98f-4934-8c9a-5aeae881acde
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7a9ebda81f013f42aeac23c9c0a8cc5a0a41f5f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651347"
---
# <a name="managing-external-tools"></a>Gerenciando ferramentas externas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

É possível chamar ferramentas externas no Visual Studio. Algumas ferramentas padrão estão disponíveis no menu **Ferramentas**, mas é possível adicionar outros executáveis de sua preferência.

## <a name="tools-available-on-the-visual-studio-tools-menu"></a>Ferramentas disponíveis no menu das Ferramentas do Visual Studio
 É possível chamar as ferramentas a seguir no menu **Ferramentas** em [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Você também pode chamá-las pelo nome na janela **Início Rápido**. Por exemplo, para chamar GuidGen.exe, digite **Criar GUID**.

1. Criar GUID: gera um GUID.

2. Pesquisa de Erro: obtém uma mensagem de erro do valor inserido. Para obter mais informações, consulte [Referência de ERRLOOK](https://msdn.microsoft.com/library/6040ffc1-2355-4a45-8998-84cbcba4ca91).

3. Ferramenta de Rastreamento da ATL/MFC: mostra mensagens de rastreamento de depuração nas fontes ATL e MFC.

4. PreEmptive Protection – Dotfuscator: protege os programas .NET contra engenharia reversa.

5. SPY++: exibe processos, threads, janelas e mensagens de janela graficamente.

6. Editor de Configuração do serviço WCF: permite criar e modificar definições de configuração para os serviços WCF.

> [!WARNING]
> Você poderá ver uma lista diferente de ferramentas externas, dependendo de qual edição do Visual Studio está instalada e o perfil de configurações aplicado. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="adding-new-tools"></a>Adicionar novas ferramentas
 É possível adicionar uma ferramenta externa ao menu **Ferramentas**. Abra a caixa de diálogo **Ferramentas externas** e clique em **Adicionar**e preencha as informações. Por exemplo, a seguinte entrada faz com que o Windows Explorer abra o diretório do arquivo atualmente aberto no Visual Studio:

1. Título: Abrir local do arquivo

2. Comando: explorer.exe

3. Argumentos: /root, "$(ItemDir)"

## <a name="arguments-for-external-tools"></a>Argumentos para ferramentas externas
 Os argumentos a seguir são variáveis do Visual Studio atribuídas ao iniciar uma ferramenta externa. Links para ferramentas externas, como Bloco de notas ou Spy++, podem estar listados no menu **Ferramentas** com a caixa de diálogo Ferramentas Externas.

> [!NOTE]
> A barra de status do IDE exibe as variáveis Linha atual e Coluna atual para indicar a localização do ponto de inserção no Editor de Código ativo. A variável Texto atual retorna o texto ou o código selecionado nesse local.

|Name|Argumento|Descrição|
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
|Diretório binário|$(BinDir)|O local final do binário que está sendo criado (definido como unidade + caminho). Por exemplo:** \\ . ..\My Documentos\Visual Studio \<Version> \\<ProjectName \> \bin\Debug**|
|Diretório do projeto|$(ProjDir)|O diretório do projeto atual (unidade + caminho).|
|Nome do arquivo de projeto|$(ProjFileName)|O nome de arquivo do projeto atual (unidade + caminho + nome de arquivo).|
|Diretório da solução|$(SolutionDir)|O diretório da solução atual (unidade + caminho).|
|Nome de arquivo da solução|$(SolutionFileName)|O nome de arquivo da solução atual (unidade + caminho + nome de arquivo).|

## <a name="see-also"></a>Consulte Também
 [Ferramentas de Build do C/C++](https://msdn.microsoft.com/library/48d9daf4-6bbf-473a-8ce2-bf2923b69f80)
