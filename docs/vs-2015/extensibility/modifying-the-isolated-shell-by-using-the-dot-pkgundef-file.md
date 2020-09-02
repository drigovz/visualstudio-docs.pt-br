---
title: Modificar o Shell isolado usando o. Arquivo Pkgundef | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: eab02fe900e96ba37c63faae535974788f99ba78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538378"
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>Modificar o Shell isolado usando o arquivo .Pkgundef
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode modificar o arquivo. pkgundef para excluir entradas de registro especificadas de um aplicativo de shell isolado. Normalmente, na primeira vez que um aplicativo é iniciado em um computador, o Shell do Visual Studio copia as entradas de registro existentes do Visual Studio para a chave do registro raiz do aplicativo. Isso inclui todas as referências a VSPackages atualmente instaladas.  
  
 Para excluir uma entrada de Registro específica de um aplicativo de shell isolado, adicione ao arquivo Application. pkgundef a chave do pacote seguida pela entrada. As chaves e as entradas são representadas da mesma forma que no arquivo. pkgdef; ou seja, como [$RootKey $] ou [$RootKey $ \\ *subkey*] e "*entry*" =*Value*, em que *subkey* é a subchave a ser afetada, *entry* é a entrada a ser removida e *Value* é `""` ou `dword:00000000` .  
  
 Para excluir várias entradas de uma chave do registro, basta listar a chave uma vez, seguida de uma linha para cada entrada a ser excluída.  
  
 Para excluir uma chave de registro inteira de um aplicativo de shell isolado, adicione a chave ao arquivo Application. pkgundef, mas não especifique nenhuma entrada de registro para essa chave.  
  
 Você pode adicionar comentários ao arquivo. pkgundef. Um comentário de linha única deve ter duas barras como os dois primeiros caracteres.  
  
 Por exemplo, para remover a **conexão ao banco de dados** e **conectar-se para atender aos** comandos do r no menu **ferramentas** , você pode remover o comentário da linha:  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 e adicione a linha:  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 para o arquivo. pkgundef do aplicativo.  
  
## <a name="see-also"></a>Consulte Também  
 [GUIDs de pacote de recursos do Visual Studio](../extensibility/package-guids-of-visual-studio-features.md)   
 [Personalizar o Shell isolado](../extensibility/customizing-the-isolated-shell.md)
