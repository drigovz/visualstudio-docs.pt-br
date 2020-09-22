---
title: Parâmetros do ponto de entrada do Shell isolado (C++) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], isolated mode%2C Start entry point
- Visual Studio shell, isolated mode%2C Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9e736343212c4bf6acd833f5740b996c6c032c3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838661"
---
# <a name="isolated-shell-entry-point-parameters-c"></a>Parâmetros de ponto de entrada do Shell isolado (C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando um aplicativo baseado em shell do Visual Studio é iniciado, ele chama o ponto de entrada inicial do shell do Visual Studio. As configurações a seguir podem ser substituídas na chamada para o ponto de entrada inicial do Shell. Para obter uma descrição de cada configuração, consulte [. Arquivos pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
- AddinsAllowed  
  
- AllowsDroppedFilesOnMainWindow  
  
- AppName  
  
- CommandLineLogo  
  
- DefaultPage  
  
- DefaultProjectsLocation  
  
- DefaultSearchPage  
  
- DefaultUserFilesFolderRoot  
  
- DisableOutputWindow  
  
- HideMiscellaneousFilesByDefault  
  
- HideSolutionConcept  
  
- NewProjDlgInstalledTemplatesHdr  
  
- NewProjDlgSlnTreeNodeTitle  
  
- SolutionFileCreatorIdentifier  
  
- SolutionFileExt  
  
- UserFilesSubFolderName  
  
- UserOptsFileExt  
  
  O modelo isolado do shell do Visual Studio cria um arquivo de origem, *SolutionName*. cpp, em que *SolutionName* é o nome da solução para o aplicativo. Esse arquivo define o ponto de entrada principal para o aplicativo, a função _tWinMain. Essa função invoca o ponto de entrada inicial do Shell.  
  
  Você pode alterar o comportamento do aplicativo alterando essas configurações quando o aplicativo é iniciado.  
  
## <a name="parameters"></a>Parâmetros  
 O ponto de entrada inicial do shell do Visual Studio define cinco parâmetros. Não altere os quatro primeiros parâmetros. O quinto parâmetro usa uma lista de substituição de configurações. O ponto de entrada inicial do Shell é chamado a partir do ponto de entrada principal de um aplicativo.  
  
 O ponto de entrada inicial do Shell tem a assinatura a seguir.  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 Se você não quiser substituir as configurações do aplicativo, deixe o valor do parâmetro de substituição de configurações como um ponteiro nulo.  
  
 Para substituir uma ou mais configurações, passe uma cadeia de caracteres Unicode que contém as configurações a serem substituídas. A cadeia de caracteres é uma lista separada por ponto-e-vírgula de pares nome-valor. Cada par contém o nome da configuração a ser substituída, seguida por um sinal de igual (=), seguido pelo valor a ser aplicado à configuração.  
  
> [!NOTE]
> Não inclua espaço em branco nas cadeias de caracteres Unicode.  
  
 Para configurações boolianas, as cadeias de caracteres a seguir representam o valor true; todas as outras cadeias de caracteres representam o valor false. Essas cadeias de caracteres não diferenciam maiúsculas de minúsculas.  
  
- \+  
  
- 1  
  
- -1  
  
- on  
  
- true  
  
- sim  
  
## <a name="example"></a>Exemplo  
 Para desabilitar os suplementos e alterar o local dos projetos padrão para seu aplicativo, você pode definir o último parâmetro como "AddinsAllowed = false; DefaultProjectsLocation =%USERPROFILE%\temp".  
  
## <a name="see-also"></a>Consulte Também  
 [Personalizando o Shell isolado](../extensibility/customizing-the-isolated-shell.md)   
 [Arquivos .Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
