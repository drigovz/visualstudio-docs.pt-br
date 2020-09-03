---
title: Galerias particulares | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 895fbef5459de75c7ccdc6a090fc30ec27a030f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "81444913"
---
# <a name="private-galleries"></a>Galerias privadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode compartilhar os controles, modelos e ferramentas que você desenvolve postando-os em uma *galeria privada* na intranet para sua organização, da seguinte maneira:  
  
- Crie um Feed Atom (RSS) para um local central configurado adequadamente (repositório) em sua intranet. Para obter mais informações, consulte [como: criar um Feed Atom para uma galeria privada](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).  
  
- Distribua um arquivo. pkgdef que descreve a galeria privada. Recomendamos essa configuração para os administradores que desejam conectar uma galeria privada a vários computadores ao mesmo tempo.  
  
## <a name="adding-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Adicionando uma galeria privada a extensões e atualizações no Visual Studio  
 Quando uma galeria privada está disponível, você pode adicioná-la a **extensões e atualizações** no Visual Studio.  
  
 ![Caixa de diálogo Adicionar do Gerenciador de extensões](../extensibility/media/em-adddialog.png "EM_AddDialog")  
  
#### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Para adicionar uma galeria privada a extensões e atualizações  
  
1. Na barra de menus, escolha **ferramentas**, **Opções**.  
  
2. No nó **ambiente** , selecione **extensões e atualizações**.  
  
3. Clique no botão **Adicionar**.  
  
4. No campo **nome** , insira um nome para a galeria privada, por exemplo, `My Gallery` .  
  
5. No campo **URL** , insira a URL do Feed Atom ou do site do SharePoint que está hospedando a galeria privada.  
  
    1. Se o host for um Feed Atom que se conecta à galeria privada, a URL seria semelhante a esta: `http://www.mywebsite/mygallery/atom.xml` .  Essa URL pode se referir a um arquivo ou a um caminho de rede.  
  
    2. Se o host for um site do SharePoint, a URL seria semelhante a esta: `http://mysharepoint/sites/mygallery/forms/AllItems.aspx` .  
  
### <a name="managing-private-galleries"></a>Gerenciando galerias particulares  
 Um administrador pode disponibilizar uma galeria privada para vários computadores ao mesmo tempo, modificando o registro do sistema em cada computador. Para fazer isso, crie um arquivo. pkgdef que descreva as novas chaves do registro e seus valores.  O formato desse arquivo é o seguinte.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=VSGallery|Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Para obter mais informações, consulte [como: gerenciar uma galeria privada usando configurações do registro](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).  
  
## <a name="installing-extensions-from-a-private-gallery"></a>Instalando extensões de uma galeria privada  
 Você pode pesquisar e instalar extensões do Visual Studio de uma galeria privada em **extensões e atualizações**. As etapas a seguir usam uma galeria privada chamada `My Gallery` .  
  
 ![Gerenciador de extensões instalando a galeria privada](../extensibility/media/em.png "EM_")  
  
#### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Para procurar e instalar extensões de uma galeria privada  
  
1. Na barra de menus, escolha **Ferramentas**, **Extensões e Atualizações**.  
  
2. No painel esquerdo, selecione **extensões online**e, em seguida, selecione **minha galeria**.  
  
3. No painel direito, selecione uma extensão e, em seguida, escolha o botão **baixar** .  
  
## <a name="updating-extensions-from-a-private-gallery"></a>Atualizando extensões de uma galeria privada  
 À medida que novas versões das extensões do Visual Studio são publicadas na galeria privada, você pode atualizar as extensões que você instalou. As etapas a seguir usam uma galeria privada chamada `My Repository` .  
  
 ![Atualização da galeria privada do Gerenciador de extensões](../extensibility/media/em-update.png "EM_Update")  
  
#### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Para atualizar uma extensão instalada de uma galeria privada  
  
1. Na barra de menus, escolha **Ferramentas**, **Extensões e Atualizações**.  
  
2. No painel esquerdo, selecione **atualizações**e, em seguida, selecione **meu repositório**.  
  
3. No painel direito, selecione uma extensão e, em seguida, escolha o botão **Atualizar** .  
  
## <a name="see-also"></a>Consulte Também  
 [Localizando e usando extensões do Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)   
 [Enviar extensões do Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
