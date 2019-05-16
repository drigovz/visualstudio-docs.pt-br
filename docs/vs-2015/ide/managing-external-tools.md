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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e568286a5e17b13b5009eccf01988d458fc9cd47
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686959"
---
# <a name="managing-external-tools"></a>Gerenciando ferramentas externas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

É possível chamar ferramentas externas no Visual Studio. Algumas ferramentas padrão estão disponíveis no menu **Ferramentas**, mas é possível adicionar outros executáveis de sua preferência.  
  
## <a name="tools-available-on-the-visual-studio-tools-menu"></a>Ferramentas disponíveis no menu das Ferramentas do Visual Studio  
 É possível chamar as ferramentas a seguir no menu **Ferramentas** em [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Você também pode chamá-las pelo nome na janela **Início Rápido**. Por exemplo, para chamar GuidGen.exe, digite **Criar GUID**.  
  
1. Criar GUID: gera um GUID.  
  
2. Pesquisa de Erro: obtém uma mensagem de erro do valor inserido. Para obter mais informações, consulte [Referência de ERRLOOK](https://msdn.microsoft.com/library/6040ffc1-2355-4a45-8998-84cbcba4ca91).  
  
3. Ferramenta de Rastreamento da ATL/MFC: mostra mensagens de rastreamento de depuração nas fontes ATL e MFC.  
  
4. PreEmptive Protection – Dotfuscator: Protege os programas .NET contra engenharia reversa.  
  
5. SPY + +: Exibe graficamente os processos, threads, windows e as mensagens da janela.  
  
6. Editor de configuração de serviço do WCF: Permite que você criar e modificar definições de configuração para serviços WCF.  
  
> [!WARNING]
> Você poderá ver uma lista diferente de ferramentas externas, dependendo de qual edição do Visual Studio está instalada e o perfil de configurações aplicado. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="adding-new-tools"></a>Adicionar novas ferramentas  
 É possível adicionar uma ferramenta externa ao menu **Ferramentas**. Abra a caixa de diálogo **Ferramentas Externas**, clique em **Adicionar** e, em seguida, preencha as informações. Por exemplo, a seguinte entrada faz com que o Windows Explorer abra o diretório do arquivo atualmente aberto no Visual Studio:  
  
1. Título: Abrir local do arquivo  
  
2. Comando: explorer.exe  
  
3. Argumentos: /root, "$(ItemDir)"  
  
## <a name="arguments-for-external-tools"></a>Argumentos para ferramentas externas  
 Os argumentos a seguir são variáveis do Visual Studio atribuídas ao iniciar uma ferramenta externa. Links para ferramentas externas, como Bloco de notas ou Spy++, podem estar listados no menu **Ferramentas** com a caixa de diálogo Ferramentas Externas.  
  
> [!NOTE]
> A barra de status do IDE exibe as variáveis Linha atual e Coluna atual para indicar a localização do ponto de inserção no Editor de Código ativo. A variável Texto atual retorna o texto ou o código selecionado nesse local.  
  
|Nome|Argumento|Descrição|  
|----------|--------------|-----------------|  
|Caminho do item|$(ItemPath)|O nome de arquivo completo do arquivo atual (unidade + caminho + nome de arquivo).|  
|Diretório do item|$(ItemDir)|O diretório do arquivo atual (unidade + caminho).|  
|Nome de Arquivo do Item|$(ItemFilename)|O nome de arquivo do arquivo atual (nome de arquivo).|  
|Extensão de item|$(ItemExt)|A extensão de nome de arquivo do arquivo atual.|  
|Linha atual|$(CurLine)|A posição da linha atual do cursor na janela de código.|  
|Coluna atual|$(CurCol)|A posição da coluna atual do cursor na janela de código.|  
|Texto atual|$(CurText)|O texto selecionado.|  
|Caminho de destino|$(TargetPath)|O nome de arquivo completo do item a ser criado (unidade + caminho + nome de arquivo).|  
|Diretório de Destino|$(TargetDir)|O diretório do item a ser criado.|  
|Nome de Destino|$(TargetName)|O nome de arquivo do item a ser criado.|  
|Extensão de Destino|$(TargetExt)|A extensão de nome de arquivo do item a ser criada.|  
|Diretório binário|$(BinDir)|O local final do binário que está sendo criado (definido como unidade + caminho). Por exemplo: **\\...\My Documents\Visual Studio \<Versão>\\<ProjectName\>\bin\debug**|  
|Diretório do Projeto|$(ProjDir)|O diretório do projeto atual (unidade + caminho).|  
|Nome do arquivo de projeto|$(ProjFileName)|O nome de arquivo do projeto atual (unidade + caminho + nome de arquivo).|  
|Diretório da solução|$(SolutionDir)|O diretório da solução atual (unidade + caminho).|  
|Nome de arquivo da solução|$(SolutionFileName)|O nome de arquivo da solução atual (unidade + caminho + nome de arquivo).|  
  
## <a name="see-also"></a>Consulte também  
 [Ferramentas de build de C/C++](https://msdn.microsoft.com/library/48d9daf4-6bbf-473a-8ce2-bf2923b69f80)
