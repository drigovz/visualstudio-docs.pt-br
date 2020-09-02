---
title: SDK de acesso à interface de depuração | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ddaea95bc879364de99c0ec01213cda30fa4e7d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197617"
---
# <a name="debug-interface-access-sdk"></a>SDK de Acesso à Interface de Depuração
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O Microsoft Debug interface Access Software Development Kit (DIA SDK) fornece acesso a informações de depuração armazenadas em arquivos do banco de dados do programa (. pdb) gerados pelas ferramentas do Microsoft CreateCompiler. Como o formato do arquivo. pdb gerado pelas ferramentas do compilador subpassa pela revisão constante, expor o formato é impraticável. Usando a API do DIA, você pode desenvolver aplicativos que pesquisem e procurem informações de depuração armazenadas em um arquivo. pdb. Tais aplicativos poderiam, por exemplo, informações de rastreamento de pilha de relatório e análise de dados de desempenho.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Introdução](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)  
 Fornece uma visão geral dos recursos de DIA SDK e especifica onde o DIA SDK é instalado, bem como os arquivos de cabeçalho e biblioteca necessários.  
  
 [Consultando o arquivo .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Fornece instruções sobre como usar a API do DIA para consultar o arquivo. pdb.  
  
 [Símbolos e marcações de símbolos](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)  
 Discute como símbolos e marcas de símbolo são usados na API de DIA.  
  
 [Referência](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
 Contém as interfaces, os métodos, as enumerações e as estruturas da API de DIA.  
  
 [Exemplo de Dia2dump](../../debugger/debug-interface-access/dia2dump-sample.md)  
 Ilustra como usar a API do DIA para pesquisar e procurar informações de depuração.  
  
 [Arquivo de origem Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)  
 Código-fonte usado pelo [exemplo de Dia2dump](../../debugger/debug-interface-access/dia2dump-sample.md) para demonstrar a API de dia.
