---
title: Introdução (debug interface Access SDK) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 54f83f00ed2e99d1541e15092cb3ee0ce9e08952
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164170"
---
# <a name="getting-started-debug-interface-access-sdk"></a>Guia de Introdução (SDK de Acesso à Interface de Depuração)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O SDK de acesso à interface de depuração (DIA) fornece documentação de instruções e um exemplo que ilustra como usar a API de DIA. Use as interfaces e métodos no DIA SDK para desenvolver aplicativos personalizados que abrem os arquivos. PDB e. dbg e pesquisem o conteúdo de símbolos, valores, atributos, endereços e outras informações de depuração. Esse SDK também fornece tabelas de referência para as propriedades associadas a símbolos encontrados em aplicativos C++.  
  
 Para usar melhor o DIA SDK, você deve estar familiarizado com o seguinte:  
  
- Linguagem de programação C++  
  
- Programação COM  
  
- IDE (ambiente de desenvolvimento integrado) do Visual Studio para compilar os exemplos  
  
  O DIA SDK normalmente é instalado com o Visual Studio e seu local padrão é *[unidade]* \Program Files\Microsoft Visual Studio 9.0 \ dia SDK. Como parte da instalação, o msdia90.dll, que implementa o DIA SDK, é registrado automaticamente, de modo que tudo o que você precisa fazer para usá-lo é incluir `dia2.h` em seu programa e vincular a `diaguids.lib` .  
  
  Cabeçalho: include\dia2.h  
  
  Library: lib\diaguids.lib  
  
  DLL: bin\msdia80.dll  
  
  IDL: idl\dia2.idl  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 Revisa a arquitetura básica do DIA.  
  
 [Consultando o arquivo .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Fornece instruções passo a passo sobre como usar a API do DIA para consultar um arquivo. pdb.  
  
## <a name="see-also"></a>Consulte Também  
 [SDK de Acesso à Interface de Depuração](../../debugger/debug-interface-access/debug-interface-access-sdk.md)
