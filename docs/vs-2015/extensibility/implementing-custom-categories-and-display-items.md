---
title: Implementando categorias personalizadas e itens de exibição | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 474d5c66507b56bea609568b6acfe9f5eff75e9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838397"
---
# <a name="implementing-custom-categories-and-display-items"></a>Implementando itens de exibição e categorias personalizadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um VSPackage pode fornecer controle das fontes e cores de seu texto para o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ambiente de desenvolvimento integrado (IDE) por meio de categorias personalizadas e itens de exibição.  
  
 As categorias personalizadas e os itens de exibição estão na página de propriedades **fontes e cores** . Para abrir a página de propriedades **fontes e cores** , no menu **ferramentas** , clique em **Opções**. Expanda **ambiente** e clique em **fontes e cores**.  
  
 Ao usar esse mecanismo, o VSPackages deve implementar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interface e suas interfaces associadas.  
  
 Em princípio, esse mecanismo pode ser usado para modificar todos os **itens de exibição** existentes e as **categorias** que os contêm. No entanto, ele não deve ser usado para modificar o **texto EditorCategory** ou seus **itens de exibição**. Para obter mais informações, consulte [visão geral de fonte e cor](../extensibility/font-and-color-overview.md).  
  
 Para implementar **categorias** personalizadas ou **itens de exibição**, um VSPackage deve:  
  
- Crie ou identifique categorias no registro.  
  
   A implementação do IDE da página de propriedades **fontes e cores** usa essas informações para consultar corretamente o serviço que dá suporte a uma determinada categoria.  
  
- Crie ou identifique grupos (opcional) no registro.  
  
   Pode ser útil definir um grupo, que representa a União de duas ou mais categorias. Se um grupo for definido, o IDE mesclará automaticamente subcategorias e distribuirá itens de exibição dentro do grupo.  
  
- Implemente o suporte a IDE.  
  
- Lide com alterações de fontes e cores.  
  
  Para obter informações, consulte [acessando configurações de fonte e cor armazenadas](../extensibility/accessing-stored-font-and-color-settings.md).  
  
## <a name="to-create-or-identify-categories"></a>Para criar ou identificar categorias  
  
- Construa um tipo especial de entrada de registro de categoria em [HKLM\SOFTWARE\Microsoft \Visual Studio \\ *\<Visual Studio version>* \FontAndColors \\ `<Category>` ]  
  
   *\<Category>* é o nome não localizado da categoria.  
  
- Preencha o registro com dois valores:  
  
  |Nome|Tipo|Dados|Descrição|  
  |----------|----------|----------|-----------------|  
  |Categoria|REG_SZ|GUID|Um GUID criado para identificar a categoria.|  
  |Pacote|REG_SZ|GUID|O GUID do serviço VSPackage que dá suporte à categoria.|  
  
  O serviço especificado no registro deve fornecer uma implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> para a categoria correspondente.  
  
## <a name="to-create-or-identify-groups"></a>Para criar ou identificar grupos  
  
- Construa um tipo especial de entrada de registro de categoria em [HKLM\SOFTWARE\Microsoft \Visual Studio \\ *\<Visual Studio version>* \FontAndColors \\ *\<group>* ]  
  
   *\<group>* é o nome não localizado do grupo.  
  
- Preencha o registro com dois valores:  
  
  |Nome|Tipo|Dados|Descrição|  
  |----------|----------|----------|-----------------|  
  |Categoria|REG_SZ|GUID|Um GUID criado para identificar o grupo.|  
  |Pacote|REG_SZ|GUID|O GUID do serviço que dá suporte à categoria.|  
  
  O serviço especificado no registro deve fornecer uma implementação de `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` para o grupo correspondente.  
  
## <a name="to-implement-ide-support"></a>Para implementar o suporte a IDE  
  
- Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A> , que retorna uma <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interface ou uma `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` interface para o IDE para cada GUID de **categoria** ou grupo fornecido.  
  
- Para cada **categoria** com suporte, um VSPackage implementa uma instância separada da <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interface.  
  
- Os métodos implementados por meio <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> do devem fornecer o IDE com:  
  
  - Listas de **itens de exibição** na **categoria.**  
  
  - Nomes localizáveis para **itens de exibição**.  
  
  - Exibir informações para cada membro da **categoria**.  
  
  > [!NOTE]
  > Cada **categoria** deve conter pelo menos um **item de exibição**.  
  
- O IDE usa a `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` interface para definir uma União de várias categorias.  
  
   Sua implementação fornece o IDE com:  
  
  - Uma lista das **categorias** que compõem um determinado grupo.  
  
  - Acesso a instâncias do que <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> dão suporte a cada **categoria** dentro do grupo.  
  
  - Nomes de grupo localizáveis.  
  
- Atualizando o IDE:  
  
   O IDE armazena em cache informações sobre as configurações **de fonte e cor** . Portanto, depois de qualquer modificação da configuração de **fonte e cor** do IDE, é aconselhável garantir que o cache esteja atualizado.  
  
  A atualização do cache é feita por meio da <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interface e pode ser executada globalmente ou apenas em itens selecionados.  
  
## <a name="to-handle-font-and-color-changes"></a>Para lidar com alterações de fonte e cor  
 Para dar suporte adequado à colorização do texto que um VSPackage exibe, o serviço de colorização que dá suporte ao VSPackage deve responder às alterações iniciadas pelo usuário feitas por meio da página de propriedades de **fontes e cores** . Um VSPackage faz isso por meio de:  
  
- Manipulação de eventos gerados pelo IDE implementando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> interface.  
  
     O IDE chama o método apropriado após as modificações de usuário da página **fontes e cores** . Por exemplo, ele chamará o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A> método se uma nova fonte for selecionada.  
  
     - ou -  
  
- Sondando o IDE em busca de alterações.  
  
     Isso pode ser feito por meio da interface implementada pelo sistema <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> . Embora principalmente o suporte à persistência, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> método pode ser usado para obter informações de fonte e cor para **itens de exibição**. Para obter mais informações, consulte [acessando as configurações de fonte e cor armazenadas](../extensibility/accessing-stored-font-and-color-settings.md).  
  
    > [!NOTE]
    > Para garantir que os resultados obtidos pela sondagem estejam corretos, pode ser útil usar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interface para determinar se uma liberação e atualização de cache são necessárias antes de chamar os métodos de recuperação da <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface.  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 [Obtendo informações de fonte e cor para a colorização de texto](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Acessando configurações de fonte e de cor armazenadas](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Como acessar as fontes internas e o esquema de cores](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)   
 [Visão geral de cor e de fonte](../extensibility/font-and-color-overview.md)
