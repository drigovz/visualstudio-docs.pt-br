---
title: Acessando configurações de fonte e de cor armazenadas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fbb2f118d903eae2124e705f14c7aa7b51bf9c4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821837"
---
# <a name="accessing-stored-font-and-color-settings"></a>Acessando as configurações de cores e fontes armazenadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE (ambiente de desenvolvimento integrado) armazena configurações modificadas para fontes e cores no registro. Você pode usar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface para acessar essas configurações.  
  
## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>Para iniciar a persistência de estado de fontes e cores  
 As informações de fonte e cor são armazenadas por categoria no seguinte local do registro: [HKCU\SOFTWARE\Microsoft \Visual Studio \\ *\<Visual Studio version>* \FontAndColors \\ *\<CategoryGUID>* ], em que *\<CategoryGUID>* é o GUID da categoria.  
  
 Portanto, para iniciar a persistência, um VSPackage deve:  
  
- Obtenha uma <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface chamando `QueryService` o provedor de serviços global.  
  
     `QueryService` deve ser chamado usando um argumento de ID de serviço de `SID_SVsFontAndColorStorage` e um argumento de ID de interface de `IID_IVsFontAndColorStorage` .  
  
- Use o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> método para abrir uma categoria a ser persistida usando o GUID da categoria e um sinalizador de modo como argumentos.  
  
  O modo, especificado pelo `fFlags` argumento, é construído a partir de valores na <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> enumeração. Este modo controla:  

  - As configurações que podem ser acessadas por meio da <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface.  

  - Todas as configurações ou apenas aquelas que os usuários modificam e que são recuperáveis por meio da <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface.  

  - A maneira de propagar as alterações para as configurações do usuário.  

  - O formato dos valores de cor que são usados.  

## <a name="to-use-state-persistence-of-fonts-and-colors"></a>Para usar a persistência de estado de fontes e cores  
 A persistência de fontes e cores envolve:  
  
- Sincronizando as configurações do IDE com as configurações armazenadas no registro.  
  
- Propagando informações de modificação do registro.  
  
- Configuração e recuperação de configurações armazenadas no registro.  
  
  A sincronização da configuração de armazenamento com as configurações do IDE é amplamente transparente. O IDE subjacente grava automaticamente as configurações atualizadas para **itens de exibição** nas entradas de registro das categorias.  
  
  Se vários VSPackages compartilharem uma determinada categoria, um VSPackage deverá exigir que os eventos sejam gerados quando os métodos da <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface forem usados para modificar as configurações armazenadas do registro.  
  
  Por padrão, a geração de eventos não está habilitada. Para habilitar a geração de eventos, uma categoria deve ser aberta usando o <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> . Isso faz com que o IDE chame o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> método apropriado que um VSPackage implementa.  
  
> [!NOTE]
> As modificações por meio da página de propriedades **Font e Color** geram eventos independentes do <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> . Você pode usar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interface para determinar se uma atualização das configurações de fonte e cor em cache é necessária antes de chamar os métodos da <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> classe.  
  
### <a name="storing-and-retrieving-information"></a>Armazenando e recuperando informações  
 Para obter ou configurar informações que um usuário pode modificar para um item de exibição nomeado em uma categoria aberta, VSPackages chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> os <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> métodos e.  
  
 Informações sobre atributos de fonte para uma determinada categoria são obtidas usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> os <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> métodos e.  
  
> [!NOTE]
> O `fFlags` argumento que é passado para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> método quando essa categoria foi aberta define o comportamento dos <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> métodos e. Por padrão, esses métodos retornam apenas informações aboutdisplay itemsthat foram alteradas. No entanto, se uma categoria for aberta usando o <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> sinalizador, os itens de exibição atualizados e inalterados poderão ser acessados pelo <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> e pelo <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> .  
  
 Por padrão, somente as informações de **itens de exibição** alterados são mantidas no registro. A <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface não pode ser usada para recuperar todas as configurações de fontes e cores.  
  
> [!NOTE]
> O <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> e os <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> métodos retornam REGDB_E_KEYMISSING, (0x80040152L) quando você os usa para recuperar informações sobre itens de **exibição**inalterados.  
  
 As configurações de todos os **itens de exibição** em uma determinada **categoria** podem ser obtidas usando os métodos da `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` interface.  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>   
 [Implementando itens de exibição e categorias personalizadas](../extensibility/implementing-custom-categories-and-display-items.md)
