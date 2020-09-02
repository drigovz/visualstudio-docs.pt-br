---
title: 'Como: gerenciar uma galeria privada usando configurações do registro | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a55b7aa486edfd3775b12dca9d143c2e5f280884
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204151"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Como gerenciar uma galeria privada usando as configurações do Registro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se você for um administrador ou o desenvolvedor de uma extensão de shell isolada, poderá controlar o acesso aos controles, modelos e ferramentas na galeria do Visual Studio, na Galeria de exemplos ou nas galerias particulares. Para tornar uma galeria disponível ou indisponível, crie um arquivo. pkgdef que descreva as chaves de registro modificadas e seus valores.  
  
## <a name="managing-private-galleries"></a>Gerenciando galerias particulares  
 Você pode criar um arquivo. pkgdef para controlar o acesso a galerias em vários computadores. Esse arquivo deve ter o formato a seguir.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom Feed|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 A `Repositories` chave refere-se à galeria a ser habilitada ou desabilitada. A galeria do Visual Studio e a Galeria de exemplos usam os seguintes GUIDs de repositório:  
  
- Galeria do Visual Studio: 0F45E408-7995-4375-9485-86B8DB553DC9  
  
- Galeria de exemplos: AEB9CB40-D8E6-4615-B52C-27E307F8506C  
  
  O `Disabled` valor é opcional. Por padrão, uma galeria está habilitada.  
  
  O `Priority` valor determina a ordem na qual as galerias são listadas na caixa de diálogo opções. A galeria do Visual Studio tem a prioridade 10 e a Galeria de exemplos tem a prioridade 20. As galerias privadas começam com a prioridade 100. Se várias galerias tiverem o mesmo valor de prioridade, a ordem na qual eles aparecem será determinada pelos valores de seus `DisplayName` atributos localizados.  
  
  O `Protocol` valor é necessário para galerias baseadas em Atom ou no SharePoint.  
  
  `DisplayName`Ou ambos, `DisplayNameResourceID` e `DisplayNamePackageGuid` devem ser especificados. Se todos forem especificados, o `DisplayNameResourceID` par e `DisplayNamePackageGuid` será usado.  
  
## <a name="disabling-the-visual-studio-gallery-using-a-pkgdef-file"></a>Desabilitando a galeria do Visual Studio usando um arquivo. pkgdef  
 Você pode desabilitar uma galeria em um arquivo. pkgdef. A seguinte entrada desabilita a galeria do Visual Studio:  
  
```  
[$RootPath$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 A seguinte entrada desabilita a Galeria de exemplos:  
  
```  
[$RootPath$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Galerias privadas](../extensibility/private-galleries.md)
