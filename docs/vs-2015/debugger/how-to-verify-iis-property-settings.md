---
title: 'Como: Verificar as configurações de propriedade do IIS | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- IIS, property settings
- debugging Web applications, troubleshooting
- IIS administration tool
- Web applications, setting properties
- properties [debugger], setting with IIS administration tool
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f5e9915f08ac7496b6a780ca721b2519a061c5cb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60076922"
---
# <a name="how-to-verify-iis-property-settings"></a>Como: Verificar as configurações de propriedade do IIS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode definir as propriedades de um aplicativo Web usando a ferramenta de administração do IIS. Essas propriedades devem ser definidas corretamente para que o aplicativo seja executado, de modo que verificar essas configurações geralmente é uma etapa necessária na solução de problemas.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-check-iis-settings-for-the-web-application"></a>Para verificar as configurações do IIS para o aplicativo Web  
  
1. Abra o **ferramentas administrativas** janela: Sobre o **inicie** , aponte para **programas**e, em seguida, clique em **ferramentas administrativas**. Se **Ferramentas Administrativas** não aparecer no menu **Programas**, procure no **Painel de Controle**.  
  
    - No Windows 2000, selecione **Gerenciador de Serviços de Internet**.  
  
    - No Windows XP, selecione **Serviços de Informações da Internet**.  
  
    - No Windows Server 2003, clique duas vezes em **Gerenciar o servidor**.  
  
         A janela **Gerenciar o servidor** é aberta. Em **Servidor de Aplicativos**, clique em **Gerenciar esse servidor de aplicativos**.  
  
         A janela **Servidor de Aplicativos** é aberta. Abra o nó **Gerenciador dos Serviços de Informações da Internet (IIS)** no painel esquerdo.  
  
2. Na caixa de diálogo, clique no nó de controle de árvore para seu computador. Clique no nó **Sites** e selecione o nó do aplicativo Web. Será um nó de sites e, portanto, um irmão do nó **Site Padrão** ou um nó de diretório virtual abaixo de um nó de site existente.  
  
3. Clique com o botão direito do mouse no aplicativo Web e, no menu de atalho, clique em **Propriedades**.  
  
4. Verifique as configurações de segurança para o aplicativo Web:  
  
    1. Na janela **Propriedades** do aplicativo Web, clique na guia **Segurança de Diretório** e clique em **Editar**.  
  
    2. Na caixa de diálogo **Métodos de Autenticação**, selecione **Habilitar Acesso Anônimo** e **Autenticação integrada do Windows** se já não estiverem selecionados.  
  
    3. Clique em **OK** para fechar a caixa de diálogo **Métodos de Autenticação**.  
  
5. Para um aplicativo do servidor ATL, verifique se o verbo DEBUG está associado à extensão ISAPI. Para obter mais informações, confira [Como: Associar o verbo DEBUG com extensão](http://msdn.microsoft.com/50d261d3-4bd4-41c0-b44e-3591086f121e).  
  
6. Para um aplicativo do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], verifique se a pasta virtual para o aplicativo tem um Nome de Aplicativo definido no **Gerenciador de IIS (Serviços de Informações da Internet)**, **Gerenciador de Serviços de Internet** ou **Serviços de Informações da Internet**.  
  
    1. Na janela **Propriedades** do aplicativo Web, selecione a guia **Diretório** se o aplicativo estiver em um diretório virtual ou a guia **Diretório Base** se o aplicativo estiver em um site.  
  
    2. Verifique se o nome no **Caminho Local** corresponde ao nome do diretório em que o aplicativo foi implantado de fato.  
  
    3. Em **Configurações do Aplicativo**, digite o nome do diretório raiz que contém o aplicativo.  
  
    4. Clique em **OK** para fechar a caixa de diálogo **Propriedades**.  
  
7. Para um aplicativo do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], clique na guia **ASP.NET** e verifique se a versão correta do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] está especificada.  
  
8. Clique em **OK** para fechar a caixa de diálogo **Propriedades**.  
  
9. Clique em **OK** para fechar a caixa de diálogo **Gerenciador de IIS (Serviços de Informações da Internet)**, **Gerenciador de Serviços de Internet** ou **Serviços de Informações da Internet**.  
  
## <a name="see-also"></a>Consulte também  
 [Solução de problemas](../debugger/debugging-web-applications-troubleshooting.md)
