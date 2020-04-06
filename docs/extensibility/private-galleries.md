---
title: Galerias Privadas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4056e4dedf06ffe86755bf946c77032d6f6782dd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702034"
---
# <a name="private-galleries"></a>Galerias privadas
Você pode compartilhar os controles, modelos e ferramentas que você desenvolve postando-os em uma *galeria privada* na intranet para sua organização, da seguinte forma:

- Crie um feed Atom (RSS) para um local central configurado adequadamente (repositório) em sua intranet. Para obter mais informações, consulte [Como: Criar um feed átomo para uma galeria privada](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

- Distribua um arquivo *.pkgdef* que descreva a galeria privada. Recomendamos essa configuração para administradores que desejam conectar uma galeria privada a muitos computadores ao mesmo tempo.

## <a name="add-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Adicione uma galeria privada às extensões e atualizações no Visual Studio
 Quando uma galeria privada estiver disponível, você pode adicioná-la a **Extensões e Atualizações** no Visual Studio.

 ![Gerenciador de extensão adicionar diálogo](../extensibility/media/em_adddialog.png "EM_AddDialog")

### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Para adicionar uma galeria privada a extensões e atualizações

1. Na barra de menus, escolha **Opções de** > **ferramentas**.

2. No nó **Ambiente,** selecione **Extensões e Atualizações**.

3. Clique no botão **Adicionar**.

4. No **campo Nome,** digite um nome para `My Gallery`a galeria privada, por exemplo, .

5. No campo **URL,** digite a URL do feed do Átomo ou do site SharePoint que hospeda a galeria privada.

    1. Se o host for um feed do Átomo que se conecta à http://www.mywebsite/mygallery/atom.xmlgaleria privada, a URL se assemelharia a esta: .  Esta URL pode se referir a um arquivo ou a um caminho de rede.

    2. Se o host for um site do SharePoint, a URL se assemelharia a este: http://mysharepoint/sites/mygallery/forms/AllItems.aspx.

### <a name="manage-private-galleries"></a>Gerencie galerias privadas
 Um administrador pode disponibilizar uma galeria privada para vários computadores ao mesmo tempo modificando o registro do sistema em cada computador. Para isso, crie um arquivo *.pkgdef* que descreva as novas chaves de registro e seus valores.  O formato deste arquivo é o seguinte.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 Para obter mais informações, consulte [Como gerenciar uma galeria privada usando configurações de registro](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).

## <a name="install-extensions-from-a-private-gallery"></a>Instale extensões de uma galeria privada
 Você pode pesquisar e instalar extensões do Visual Studio a partir de uma galeria privada em **Extensões e Atualizações**. As etapas a seguir `My Gallery`usam uma galeria privada chamada .

 ![Gerenciador de extensão instalando galeria privada](../extensibility/media/em_.png "EM_")

### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Para procurar e instalar extensões de uma galeria privada

1. Na barra de menus, escolha**Extensões e Atualizações de** **Ferramentas** > .

2. No painel esquerdo, selecione **Extensões Online**e selecione **Minha Galeria**.

3. No painel direito, selecione uma extensão e escolha o botão **Baixar.**

## <a name="update-extensions-from-a-private-gallery"></a>Atualizar extensões de uma galeria privada
 À medida que novas versões das extensões do Visual Studio são publicadas na galeria privada, você pode atualizar as extensões que você instalou. As etapas a seguir `My Repository`usam uma galeria privada chamada .

 ![Atualização da galeria privada do gerenciador de extensões](../extensibility/media/em_update.png "EM_Update")

### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Para atualizar uma extensão instalada de uma galeria privada

1. Na barra de menus, escolha**Extensões e Atualizações de** **Ferramentas** > .

2. No painel esquerdo, selecione **Atualizações**e selecione **Meu repositório**.

3. No painel direito, selecione uma extensão e escolha o botão **Atualizar.**

## <a name="see-also"></a>Confira também
- [Localizar e usar extensões do Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
- [Extensões do Ship Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
