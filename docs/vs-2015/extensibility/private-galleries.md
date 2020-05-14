---
title: Galerias Privadas | Microsoft Docs
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
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444913"
---
# <a name="private-galleries"></a>Galerias privadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode compartilhar os controles, modelos e ferramentas que você desenvolve postando-os em uma *galeria privada* na intranet para sua organização, da seguinte forma:  
  
- Crie um feed Atom (RSS) para um local central configurado adequadamente (repositório) em sua intranet. Para obter mais informações, consulte [Como: Criar um feed de átomos para uma galeria privada](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).  
  
- Distribua um arquivo .pkgdef que descreva a galeria privada. Recomendamos essa configuração para administradores que desejam conectar uma galeria privada a muitos computadores ao mesmo tempo.  
  
## <a name="adding-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Adicionando uma Galeria Privada a Extensões e Atualizações no Visual Studio  
 Quando uma galeria privada estiver disponível, você pode adicioná-la a **Extensões e Atualizações** no Visual Studio.  
  
 ![Gerenciador de extensão adicionar diálogo](../extensibility/media/em-adddialog.png "EM_AddDialog")  
  
#### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Para adicionar uma galeria privada a extensões e atualizações  
  
1. Na barra de menu, escolha **Ferramentas**, **Opções**.  
  
2. No nó **Ambiente,** selecione **Extensões e Atualizações**.  
  
3. Clique no botão **Adicionar**.  
  
4. No **campo Nome,** digite um nome para `My Gallery`a galeria privada, por exemplo, .  
  
5. No campo **URL,** digite a URL do feed do Átomo ou do site SharePoint que hospeda a galeria privada.  
  
    1. Se o host for um feed do Átomo que se conecta à `http://www.mywebsite/mygallery/atom.xml`galeria privada, a URL se assemelharia a esta: .  Esta URL pode se referir a um arquivo ou a um caminho de rede.  
  
    2. Se o host for um site do SharePoint, a URL se assemelharia a este: `http://mysharepoint/sites/mygallery/forms/AllItems.aspx`.  
  
### <a name="managing-private-galleries"></a>Gestão de Galerias Privadas  
 Um administrador pode disponibilizar uma galeria privada para vários computadores ao mesmo tempo modificando o registro do sistema em cada computador. Para isso, crie um arquivo .pkgdef que descreva as novas chaves de registro e seus valores.  O formato deste arquivo é o seguinte.  
  
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
  
 Para obter mais informações, [consulte Como gerenciar uma galeria privada usando configurações de registro](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).  
  
## <a name="installing-extensions-from-a-private-gallery"></a>Instalando extensões de uma galeria privada  
 Você pode pesquisar e instalar extensões do Visual Studio a partir de uma galeria privada em **Extensões e Atualizações**. As etapas a seguir `My Gallery`usam uma galeria privada chamada .  
  
 ![Gerenciador de extensão instalando galeria privada](../extensibility/media/em.png "EM_")  
  
#### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Para procurar e instalar extensões de uma galeria privada  
  
1. Na barra de menus, escolha **Ferramentas**, **Extensões e Atualizações**.  
  
2. No painel esquerdo, selecione **Extensões Online**e selecione **Minha Galeria**.  
  
3. No painel direito, selecione uma extensão e escolha o botão **Baixar.**  
  
## <a name="updating-extensions-from-a-private-gallery"></a>Atualizando extensões de uma galeria privada  
 À medida que novas versões das extensões do Visual Studio são publicadas na galeria privada, você pode atualizar as extensões que você instalou. As etapas a seguir `My Repository`usam uma galeria privada chamada .  
  
 ![Atualização da galeria privada do gerenciador de extensões](../extensibility/media/em-update.png "EM_Update")  
  
#### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Para atualizar uma extensão instalada de uma galeria privada  
  
1. Na barra de menus, escolha **Ferramentas**, **Extensões e Atualizações**.  
  
2. No painel esquerdo, selecione **Atualizações**e selecione **Meu repositório**.  
  
3. No painel direito, selecione uma extensão e escolha o botão **Atualizar.**  
  
## <a name="see-also"></a>Consulte Também  
 [Encontrando e usando extensões do Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)   
 [Enviar extensões do Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
