---
title: Como habilitar a depuração para aplicativos ASP.NET | Microsoft Docs
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
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5726e964a0db2fae1b902f54a14e206dbc03a148
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77477003"
---
# <a name="how-to-enable-debugging-for-aspnet-applications"></a>Instruções: habilitar a depuração para aplicativos ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para habilitar a depuração, você deve habilitá-la na página de **Propriedades do projeto** e no arquivo de web.config do aplicativo.  
  
> [!NOTE]  
> As caixas de diálogo e os comandos de menu encontrados podem diferir daqueles descritos na Ajuda, dependendo das configurações ativas ou edição. Para alterar suas configurações, selecione **Importar e Exportar Configurações** no menu **Ferramentas** . Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](/previous-versions/zbhkx167(v=vs.140)).  
  
### <a name="to-enable-aspnet-debugging-in-the-project-properties-visual-basicc"></a>Para habilitar a depuração ASP.NET nas propriedades de projeto (Visual Basic/C#)  
  
1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no nome de um projeto Web e selecione **Propriedades**.  
  
2. Na página Propriedades do projeto, clique na guia **Web** .  
  
3. Em **depuradores**, marque a caixa de seleção **ASP.net** .  
  
### <a name="to-enable-debugging-in-the-webconfig-file"></a>Para habilitar a depuração no arquivo web.config  
  
1. Abra o arquivo web.config usando qualquer editor de texto ou analisador XML padrão.  
  
    > [!NOTE]  
    > No entanto, você não pode acessar o arquivo remotamente usando um navegador da Web. Por razões de segurança, o [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] configura o servidor IIS da Microsoft para ajudar a impedir o acesso direto do navegador aos arquivos Web.config. Se você tentar acessar um arquivo de configuração usando um navegador, receberá o erro de acesso HTTP 403 (proibido).  
  
2. Web.config é um arquivo XML e, assim, contém as seções aninhadas marcadas por aspas. Localize o elemento `configuration/system.web/compilation`. Se o elemento de compilação não existir, crie-o.  
  
3. Se o elemento `compilation` não contiver um atributo `debug`, adicione o atributo ao elemento.  
  
4. Verifique se o valor do atributo `debug` está definido como `true`.  
  
O arquivo web.config deve parecer com o exemplo a seguir. Observe que pode haver seções entre a configuração e os elementos system.web  
  
- seções de elementos entre a configuração e os elementos system.web  
  
- seções de elementos entre system.web e os elementos de compilação  
  
- Um elemento de compilação pode conter outros atributos e elementos  
  
## <a name="example"></a>Exemplo  
  
```  
<configuration>  
    ...  
    <system.web>  
        <compilation  
            debug="true"  
            ...  
        >  
        ...  
        </compilation>  
    </system.web>  
</configuration>  
```  
  
## <a name="robust-programming"></a>Programação robusta  
[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] o detecta automaticamente quaisquer alterações em Web.config arquivos e aplica as novas definições de configuração. Você não precisa reiniciar o computador ou reiniciar o servidor IIS para que as alterações entrem em vigor.  
  
Um site pode conter vários diretórios e subdiretórios virtuais, e arquivos Web.config podem existir em cada um. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] os aplicativos herdam as configurações de Web.config arquivos em níveis mais altos no caminho da URL. Os arquivos de configuração hierárquicos permitem modificar configurações de vários aplicativos [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ao mesmo tempo, como, por exemplo, para todos os aplicativos abaixo deles na hierarquia. No entanto, se `debug` for definido em um arquivo mais baixo na hierarquia, ele substituirá o valor mais alto.  
  
Por exemplo, você pode especificar `debug="true"` em `www.microsoft.com/aaa/Web.config` , e qualquer aplicativo na pasta AAA ou em qualquer subpasta de AAA herdará essa configuração. Portanto, se seu [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplicativo estiver em `www.microsoft.com/aaa/bbb` , ele herdará essa configuração, assim como qualquer aplicativo [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] no `www.microsoft.com/aaa/ccc` , `www.microsoft.com/aaa/ddd` , e assim por diante. A única exceção será se um desses aplicativos substituir a configuração por meio de seu próprio arquivo mais baixo Web.config.  
  
Habilitar o modo de depuração afetará significativamente o desempenho do aplicativo [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Lembre-se de desabilitar o modo de depuração antes de implantar um aplicativo de versão ou conduzir medidas de desempenho.  
  
## <a name="see-also"></a>Consulte Também  
[Depurando aplicativos ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)  
