---
title: Obtendo informações de fonte e cor para a colorização de texto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8724c31accb26e478c2726dfe791256994fc95ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696852"
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>Obtenção de informações de cores e fontes para colorização de texto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O processo que renderiza ou exibe texto colorido em elementos da interface do usuário depende do tipo de projeto, da tecnologia e das preferências do desenvolvedor. A página de propriedades **fontes e cores** armazena as configurações.  
  
 A maioria das implementações que exibem texto colorido precisa das `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` interfaces associadas para apresentar, recuperar e armazenar as configurações de exibição de texto.  
  
> [!NOTE]
> Ao personalizar o editor de núcleo (que dá suporte ao **EditorCategory de texto**), é altamente recomendável que você use a tecnologia de cores no serviço de idioma. Para obter mais informações, consulte [visão geral de fonte e cor](../extensibility/font-and-color-overview.md).  
  
## <a name="getting-default-font-and-color-information"></a>Obtendo informações padrão de fonte e cor  
 Todas as configurações de **fontes e cores** de qualquer janela que exibem texto devem ser especificadas nos **itens de exibição** de uma **categoria**. Para obter mais informações, consulte [fontes e cores, ambiente, caixa de diálogo opções](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
 Para colorir, um VSPackage deve obter as configurações atuais de **fontes e cores** . Um VSPackage pode fazer isso das seguintes maneiras, dependendo de suas necessidades:  
  
- Use o mecanismo de persistência de fonte e cor para recuperar o estado armazenado ou atual. Para obter mais informações, consulte [acessando as configurações de fonte e cor armazenadas](../extensibility/accessing-stored-font-and-color-settings.md).  
  
- Use a <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interface de um serviço que fornece dados de fonte e cor para obter uma instância do <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> , se o VSPackage não for também o provedor de fontes e cores.  
  
- Implemente a interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>.  
  
  Para garantir que os resultados obtidos pela sondagem estejam atualizados, pode ser útil usar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interface para determinar se uma atualização é necessária antes de chamar os métodos de recuperação da <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interface.  
  
  Depois de obter as informações de fonte e cor, analise o texto a ser exibido para identificar os elementos que exigem a colorização e, em seguida, exiba o texto na janela usando as fontes e cores apropriadas.  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [Usando fontes e texto](https://msdn.microsoft.com/library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [Trabalhando com cores](https://msdn.microsoft.com/library/d34ff96f-241d-494f-abdd-13811ada8cd3)   
 [GDI (interface de dispositivo de gráficos)](https://msdn.microsoft.com/7e1d4540-bb2e-4257-8eee-eee376acba83)
