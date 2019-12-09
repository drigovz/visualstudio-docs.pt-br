---
title: Páginas de Propriedade, JavaScript | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- javascript.project.property.debugging.debuggertype
- javascript.project.property.debugging.requireauthentication
- javascript.project.property.outputpath
- javascript.project.property.debugging.launchapplication
- javascript.project.property.defaultlanguage
- javascript.project.property.debugging.machinename
- javascript.project.property.debugging.allowlocalnetworkloopback
ms.assetid: a05ab01f-3d5d-4675-a845-eab51807d3a3
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ffb1298981481bde063de898dc81c02dad548888
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297831"
---
# <a name="property-pages-javascript"></a>Páginas de Propriedade, JavaScript
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

As **Páginas de Propriedade** fornecem acesso às configurações do projeto. Você pode usar as páginas que aparecem nas **Páginas de Propriedade** para alterar as propriedades do projeto.

 Para acessar as propriedades do projeto, selecione um nó do projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**.

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

 As opções e páginas a seguir aparecem nas **Páginas de Propriedade**.

## <a name="configuration-and-platform-page"></a>Página de plataforma e configuração
 Use as seguintes opções para selecionar a configuração e a plataforma a exibir ou modificar.

 **Configuração** do Especifica as definições de configuração a serem exibidas ou modificadas. As configurações são **Depurar** (padrão), **Versão**, **Todas as Configurações de** ou uma configuração definida pelo usuário. Para obter mais informações, consulte [Configurações de projeto de depuração e versão](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 **Plataforma** do Especifica as configurações de plataforma a serem exibidas ou modificadas. As configurações são **Qualquer CPU** (padrão para aplicativos [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]), **x64**, **ARM**, **x86** ou uma plataforma definida pelo usuário. Para obter mais informações, consulte [Configurações de projeto de depuração e versão](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

## <a name="general-page"></a>Página Geral
 Use as seguintes opções para configurar propriedades gerais do projeto.

> [!NOTE]
> Algumas opções estão disponíveis somente em Aplicativos da Windows Store.

 **Caminho de saída** Especifica o local dos arquivos de saída para a configuração do projeto. O caminho é relativo; se você inserir um caminho absoluto, o caminho absoluto será salvo no projeto. O caminho padrão é bin\Debug.

 Quando você usa configurações de build simplificadas, o sistema do projeto determina se é necessário compilar uma versão de depuração ou de liberação. Quando você clica em **Depurar**, **Iniciar Depuração** (ou pressiona F5), o build é colocado no local de depuração, independentemente do **Caminho de saída** especificado. No entanto, o comando **Compilar Solução** no menu **Criar** a coloca no local especificado. Para habilitar as configurações de build avançadas, na barra de menus, escolha **Ferramentas**, **Opções**. Na caixa de diálogo **Opções**, expanda **Projetos e Soluções**, selecione **Geral** e desmarque a caixa de seleção **Mostrar configurações de build avançadas**. Isso lhe dá controle manual sobre todos os valores de configuração e de se uma versão de depuração ou liberação é compilada. Para obter mais informações, consulte [NIB: caixa de diálogo Geral, Projetos e Soluções, Opções](https://msdn.microsoft.com/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).

 **Idioma padrão** Especifica o idioma padrão do projeto. A opção de idioma selecionada em **Relógio, Idioma e Região** no Painel de Controle especifica o idioma preferencial do usuário. Ao especificar um idioma padrão para o projeto, certifique-se de que os recursos de idioma padrão especificado sejam usados se o idioma preferencial do usuário não corresponder aos recursos de idioma fornecidos no aplicativo.

## <a name="debug-page"></a>Página de depuração
 Use as seguintes opções para definir propriedades para o comportamento de depuração no projeto.

> [!NOTE]
> Algumas opções estão disponíveis somente em Aplicativos da Windows Store.

 **Depurador a ser iniciado** Especifica o host padrão para o depurador.

- Selecione **Computador Local** para iniciar o aplicativo no computador de host do Visual Studio. Para obter mais informações, consulte [Executando aplicativos no computador local](https://go.microsoft.com/fwlink/?LinkId=234912).

- Selecione **Simulador** para iniciar o aplicativo no Simulador. Para obter mais informações, consulte [Executando aplicativos no simulador](https://go.microsoft.com/fwlink/?LinkId=234913).

- Selecione **Computador Remoto** para iniciar o aplicativo em um computador remoto. Para obter mais informações sobre a depuração remota, consulte [Executando aplicativos em um computador remoto](https://go.microsoft.com/fwlink/?LinkId=234914).

  **Iniciar aplicativo** Especifica se o aplicativo deve ser iniciado quando você pressiona F5 ou clica em **depurar**, **Iniciar Depuração**. Selecione **Sim** para iniciar o aplicativo; caso contrário, selecione **Não**. Se você selecionar **Não**, ainda poderá depurar o aplicativo se você usar um método diferente para iniciá-lo.

  **Tipo de depurador** Especifica os tipos de código a serem depurados. Selecione **Somente Script** para depurar o código JavaScript. Selecione **Somente Gerenciado** para depurar código gerenciado pelo Common Language Runtime. Selecione **Somente Nativo** para depurar código C++. Selecione **Nativo com Script** para depurar C++ e JavaScript. Selecione **Misto (Gerenciado e Nativo)** para depurar código gerenciado e C++.

  **Permitir loopback de rede local** Especifica se o acesso ao endereço de loopback IP é permitido para teste de aplicativo. Selecione **Sim** para permitir o uso do endereço de loopback se o aplicativo cliente estiver no mesmo computador em que o aplicativo para servidores está em execução; caso contrário, selecione **Não**. Essa propriedade estará disponível somente se a propriedade **Depurador a Iniciar** estiver definida como **Computador Remoto**.

  **Nome do computador** Especifica o nome do computador remoto para hospedar o depurador. Essa propriedade estará disponível somente se **Depurador a Iniciar** estiver definido como **Computador Remoto**.

  **Exigir autenticação** Especifica se o computador remoto requer autenticação. Essa propriedade estará disponível somente se **Depurador a Iniciar** estiver definido como **Computador Remoto**.
