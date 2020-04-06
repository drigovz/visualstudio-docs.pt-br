---
title: 'Como: Gerenciar uma galeria privada usando configurações de registro | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2630fc71bea40a4d05e616ae336759ba62431a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710927"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Como: Gerenciar uma galeria privada usando configurações de registro
Se você é um administrador ou o desenvolvedor de uma extensão Shell isolada, você pode controlar o acesso aos controles, modelos e ferramentas na Visual Studio Gallery, na Galeria amostras ou em galerias privadas. Para disponibilizar uma galeria ou não, crie um arquivo *.pkgdef* que descreva as chaves de registro modificadas e seus valores.

## <a name="manage-private-galleries"></a>Gerencie galerias privadas
 Você pode criar um arquivo *.pkgdef* para controlar o acesso a galerias em vários computadores. Este arquivo deve ter o seguinte formato.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom Feed|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 A `Repositories` chave refere-se à galeria a ser ativada ou desativada. A Visual Studio Gallery e a Galeria amostras usam os seguintes GUIDs de repositório:

- Galeria Visual Studio : 0F45E408-7995-4375-9485-86B8DB553DC9

- Galeria de amostras: AEB9CB40-D8E6-4615-B52C-27E307F8506C

  O `Disabled` valor é opcional. Por padrão, uma galeria está habilitada.

  O `Priority` valor determina a ordem em que as galerias estão listadas na caixa de diálogo **Opções.** Visual Studio Gallery tem prioridade 10 e a Galeria amostras tem prioridade 20. Galerias privadas começam na prioridade 100. Se várias galerias tiverem o mesmo valor prioritário, a ordem em `DisplayName` que elas aparecem é determinada pelos valores de seus atributos localizados.

  O `Protocol` valor é necessário para galerias baseadas em Átomo ou SharePoint.

  Ou `DisplayName`ambos `DisplayNameResourceID` devem `DisplayNamePackageGuid`ser especificados. Se todos forem especificados, o par e `DisplayNameResourceID` `DisplayNamePackageGuid` o par serão usados.

## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>Desative a Visual Studio Gallery usando um arquivo .pkgdef
 Você pode desativar uma galeria em um arquivo *.pkgdef.* A entrada a seguir desativa a Visual Studio Gallery:

```
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]
"Disabled"=dword:00000001

```

 A entrada a seguir desativa a Galeria de amostras:

```
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]
"Disabled"=dword:00000001

```

## <a name="see-also"></a>Confira também
- [Galerias privadas](../extensibility/private-galleries.md)
