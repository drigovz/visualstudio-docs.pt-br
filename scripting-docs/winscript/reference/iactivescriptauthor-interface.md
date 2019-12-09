---
title: Interface IActiveScriptAuthor | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptAuthor interface
ms.assetid: df1f454d-01ee-4beb-928b-48513d07365a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed0734fa48d58a5eae779c75c838c09215ed60a0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576166"
---
# <a name="iactivescriptauthor-interface"></a>Interface IActiveScriptAuthor
Representa serviços de criação, incluindo IntelliSense e agrupamento de informações.  
  
 Além dos métodos herdados de `IUnknown`, a interface `IActiveScriptAuthor` expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|Adiciona o nome de um item de nível raiz ao namespace do mecanismo de criação de scripts. Um *item de nível raiz* é um objeto que pode conter Propriedades e métodos, e que também pode conter uma origem de evento.|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|Adiciona um Scriptlet de código como um filho do nível raiz `IScriptNode` objeto. No host, o nome totalmente qualificado do scriptlet pode ter apenas dois níveis.|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|Adiciona uma biblioteca de tipos ao namespace para o script.|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|Retorna o conjunto de caracteres de conclusão para um contexto de conclusão solicitado.|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|Retorna o scriptlet que tem os atributos especificados.|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|Retorna informações de tipo e posições de ancoragem para um determinado caractere em um bloco de código. Isso fornece informações para IntelliSense de membro, listas globais e dicas de parâmetro.|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|Retorna informações de idioma.|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|Retorna o `IScriptNode` raiz da árvore de script do autor.|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|Retorna os atributos de texto de um Scriptlet.|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|Retorna os atributos de texto de um bloco de script.|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|Retorna um valor que indica se um determinado caractere deve confirmar a conclusão de uma instrução pelo aplicativo.|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|Analisa o texto do script, adiciona o texto ao mecanismo de criação de script de criação e cria um objeto `IScriptEntry` que corresponde ao bloco de script.|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|Remove um objeto `NamedItem` do namespace do mecanismo de criação de scripts.|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|Remove uma biblioteca de tipos do namespace do mecanismo de criação de scripts.|  
  
## <a name="see-also"></a>Consulte também  
 [Active Script Authoring Interfaces](../../winscript/reference/active-script-authoring-interfaces.md)