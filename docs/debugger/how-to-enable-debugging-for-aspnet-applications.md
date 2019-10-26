---
title: Habilitar depuração para aplicativos ASP.NET | Microsoft Docs
ms.custom: ''
ms.date: 09/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: a6f20a2272214a525b00ebf07ebc6e5e803b138c
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911345"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>Depurar aplicativos ASP.NET ou ASP.NET Core no Visual Studio

Você pode depurar ASP.NET e ASP.NET Core aplicativos no Visual Studio. O processo difere entre ASP.NET e ASP.NET Core e se você o executa em IIS Express ou em um servidor IIS local.

>[!NOTE]
>As etapas e configurações a seguir se aplicam somente à depuração de aplicativos em um servidor local. A depuração de aplicativos em um servidor IIS remoto usa **anexar ao processo**e ignora essas configurações. Para obter mais informações e instruções para depuração remota de aplicativos ASP.NET no IIS, consulte [depuração remota ASP.net em um computador IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) ou [ASP.NET Core de depuração remota em um computador IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

O servidor de IIS Express interno está incluído no Visual Studio. IIS Express é o servidor de depuração padrão para projetos ASP.NET e ASP.NET Core e é pré-configurado. É a maneira mais fácil de depurar e ideal para depuração e teste inicial.

Você também pode depurar um aplicativo ASP.NET ou ASP.NET Core em um servidor IIS local (versão 8,0 ou superior) que está configurado para executar o aplicativo. Para depurar no IIS local, você deve atender aos seguintes requisitos:

<a name="iis"></a>
- Selecione o **tempo de desenvolvimento suporte do IIS** ao instalar o Visual Studio. (Se necessário, execute novamente o Instalador do Visual Studio, selecione **Modificar**e adicione este componente.)
- Executar o Visual Studio como administrador.
- Instale e configure corretamente o IIS com as versões apropriadas de ASP.NET e/ou ASP.NET Core. Para obter mais informações e instruções, consulte [iis 8,0 usando ASP.NET 3,5 e ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) ou [host ASP.NET Core no Windows com o IIS](/aspnet/core/host-and-deploy/iis/index).
- Verifique se o aplicativo é executado no IIS sem erros.

## <a name="debug-aspnet-apps"></a>Depurar aplicativos ASP.NET

IIS Express é o padrão e é pré-configurado. Se você estiver depurando no IIS local, certifique-se de atender aos [requisitos para depuração local do IIS](#iis).

1. Selecione o projeto ASP.NET no Visual Studio **Gerenciador de soluções** e clique no ícone **Propriedades** , pressione **ALT**+**Enter**ou clique com o botão direito do mouse e escolha **Propriedades**.

1. Selecione a guia **Web** .

1. No painel **Propriedades** , em **servidores**,
   - Para IIS Express, selecione **IIS Express** na lista suspensa.
   - Para IIS local,
     1. Selecione **IIS local** na lista suspensa.
     1. Ao lado do campo **URL do projeto** , selecione **criar diretório virtual**, se você ainda não tiver configurado o aplicativo no IIS.

1. Em **depuradores**, selecione **ASP.net**.

   ![Configurações do depurador ASP.NET](media/dbg-aspnet-enable-debugging2.png "Configurações do depurador ASP.NET")

1. Use o **arquivo** > **salvar os itens selecionados** ou **Ctrl**+**S** para salvar as alterações.

1. Para depurar o aplicativo, em seu projeto, defina pontos de interrupção em algum código. Na barra de ferramentas do Visual Studio, verifique se a configuração está definida como **depurar**e se o navegador que você deseja aparece em **IIS Express (\<nome do navegador >)** ou **IIS local (\<nome do navegador >)** no campo emulador.

1. Para iniciar a depuração, selecione **IIS Express (\<nome do navegador >)** ou **IIS local (\<nome do navegador >)** na barra de ferramentas, selecione **Iniciar Depuração** no menu **depurar** ou pressione **F5**. O depurador pausa nos pontos de interrupção. Se o depurador não puder atingir os pontos de interrupção, consulte [solucionar problemas de depuração](#troubleshoot-debugging).

## <a name="debug-aspnet-core-apps"></a>Depurar ASP.NET Core aplicativos

IIS Express é o padrão e é pré-configurado. Se você estiver depurando no IIS local, certifique-se de atender aos [requisitos para depuração local do IIS](#iis).

1. Selecione o projeto ASP.NET Core no Visual Studio **Gerenciador de soluções** e clique no ícone **Propriedades** , pressione **ALT**+**Enter**ou clique com o botão direito do mouse e escolha **Propriedades**.

1. Selecione a guia **Depurar**.

1. No painel **Propriedades** , ao lado de **perfil**,
   - Para IIS Express, selecione **IIS Express** na lista suspensa.
   - Para IIS local, selecione o nome do aplicativo no menu suspenso ou selecione **novo**, crie um novo nome de perfil e selecione **OK**.

1. Ao lado de **Iniciar**, selecione **IIS Express** ou **IIS** na lista suspensa.

1. Verifique se a **inicialização do navegador** está selecionada.

1. Em **variáveis de ambiente**, certifique-se de que **ASPNETCORE_ENVIRONMENT** está presente com um valor de **desenvolvimento**. Caso contrário, selecione **Adicionar** e adicione-o.

   ![ASP.NET Core configurações do depurador](../debugger/media/dbg-aspnet-enable-debugging3.png "ASP.NET Core configurações do depurador")

1. Use o **arquivo** > **salvar os itens selecionados** ou **Ctrl**+**S** para salvar as alterações.

1. Para depurar o aplicativo, em seu projeto, defina pontos de interrupção em algum código. Na barra de ferramentas do Visual Studio, verifique se a configuração está definida como **depurar**e **IIS Express**ou o novo nome do perfil do IIS, aparece no campo emulador.

1. Para iniciar a depuração, selecione **IIS Express** ou **\<nome do perfil do IIS >** na barra de ferramentas, selecione **Iniciar Depuração** no menu **depurar** ou pressione **F5**. O depurador pausa nos pontos de interrupção. Se o depurador não puder atingir os pontos de interrupção, consulte [solucionar problemas de depuração](#troubleshoot-debugging).

## <a name="troubleshoot-debugging"></a>Solucionar problemas de depuração

Se a depuração local do IIS não puder progredir para o ponto de interrupção, siga estas etapas para solucionar o problema.

1. Inicie o aplicativo Web do IIS e certifique-se de que ele seja executado corretamente. Deixe o aplicativo Web em execução.

2. No Visual Studio, selecione **depurar > anexar ao processo** ou pressione **Ctrl**+**ALT**+**P**e conecte-se ao ASP.net ou ao processo de ASP.NET Core (normalmente **w3wp. exe** ou **dotnet. exe**). Para obter mais informações, consulte [anexar ao processo](attach-to-running-processes-with-the-visual-studio-debugger.md) e [como encontrar o nome do processo de ASP.net](how-to-find-the-name-of-the-aspnet-process.md).

Se você puder se conectar e atingir o ponto de interrupção usando **Attach to Process**, mas não usando **debug** > **iniciar a depuração** ou **F5**, uma configuração provavelmente será incorreta nas propriedades do projeto. Se você usar um arquivo de HOSTs, verifique se ele também está configurado corretamente.

## <a name="configure-debugging-in-the-webconfig-file"></a>Configurar a depuração no arquivo Web. config

Os projetos ASP.NET têm arquivos *Web. config* por padrão, que contêm a configuração do aplicativo e as informações de inicialização, incluindo configurações de depuração. Os arquivos *Web. config* devem ser configurados corretamente para depuração. As configurações de **Propriedades** nas seções anteriores atualizam os arquivos *Web. config* , mas você também pode configurá-los manualmente.

> [!NOTE]
> Os projetos de ASP.NET Core não têm inicialmente arquivos *Web. config* , mas usam arquivos *appSettings. JSON* e *launchSettings. JSON* para a configuração do aplicativo e informações de inicialização. Implantar o aplicativo cria um arquivo *Web. config* ou arquivos no projeto, mas eles normalmente não contêm informações de depuração.

> [!TIP]
> O processo de implantação pode atualizar as configurações do *Web. config* , portanto, antes de tentar depurar, verifique se o *Web. config* está configurado para depuração.

**Para configurar manualmente um arquivo *Web. config* para depuração:**

1. No Visual Studio, abra o arquivo *Web. config* do projeto ASP.net.

2. *Web. config* é um arquivo XML, portanto contém seções aninhadas marcadas por marcas. Localize a seção `configuration/system.web/compilation`. (Se o elemento `compilation` não existir, crie-o.)

3. Verifique se o atributo `debug` no elemento `compilation` está definido como `true`. (Se o elemento `compilation` não contiver um atributo `debug`, adicione-o e defina-o como `true`.)

   Se você estiver usando o IIS local em vez do servidor de IIS Express padrão, verifique se o valor do atributo `targetFramework` no elemento `compilation` corresponde à estrutura no servidor IIS.

   O elemento `compilation` do arquivo *Web. config* deve ser semelhante ao exemplo a seguir:

   > [!NOTE]
   > Este exemplo é um arquivo *Web. config* parcial. Geralmente, há seções XML adicionais nos elementos `configuration` e `system.web`, e o elemento `compilation` também pode conter outros atributos e elementos.

   ```xml
   <configuration>
      ...
      <system.web>
          <compilation  debug="true"  targetFramework="4.6.1" ... >
             ...
          </compilation>
      </system.web>
   </configuration>
   ```

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] detecta automaticamente quaisquer alterações em arquivos *Web. config* e aplica as novas definições de configuração. Você não precisa reiniciar o computador ou o servidor IIS para que as alterações entrem em vigor.

Um site pode conter vários diretórios virtuais e subdiretórios, com arquivos *Web. config* em cada um. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicativos herdam definições de configuração de arquivos *Web. config* em níveis mais altos no caminho da URL. As configurações de arquivo *Web. config* hierárquicos se aplicam a todos os aplicativos [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] abaixo deles na hierarquia. Definir uma configuração diferente em um arquivo *Web. config* inferior na hierarquia substitui as configurações no arquivo superior.

Por exemplo, se você especificar `debug="true"` em <em>www.Microsoft.com/aaa/Web.config</em>, qualquer aplicativo na pasta *AAA* ou em qualquer subpasta de *AAA* herda essa configuração, exceto se um desses aplicativos substituir a configuração por seu próprio *Web. config* Grupo.

## <a name="publish-in-debug-mode-using-the-file-system"></a>Publicar no modo de depuração usando o sistema de arquivos

Há diferentes maneiras de publicar aplicativos no IIS. Estas etapas mostram como criar e implantar um perfil de publicação de depuração usando o sistema de arquivos. Para fazer isso, você deve estar executando o Visual Studio como administrador.

> [!IMPORTANT]
> Se você alterar seu código ou recompilar, deverá repetir essas etapas para republicar.

1. No Visual Studio, clique com o botão direito do mouse no projeto e escolha **publicar**.

3. Escolha **IIS, FTP, etc.** e clique em **publicar**.

    ![Publicar no IIS](media/dbg-aspnet-local-iis.png "Publicar no IIS")

4. Na caixa de diálogo **CustomProfile** , para o **método Publish**, escolha **sistema de arquivos**.

5. Para **local de destino**, selecione **procurar** ( **...** ).

   - Para ASP.NET, selecione **local IIS**, selecione o site que você criou para o aplicativo e, em seguida, selecione **abrir**.

     ![Publicar no ASP.NET no IIS](media/dbg-aspnet-local-iis1.png "Publicar ASP.NET no IIS")

   - Para ASP.NET Core, selecione **sistema de arquivos**, selecione a pasta que você configurou para o aplicativo e, em seguida, selecione **abrir**.

1. Selecione **Avançar**.

1. Em **configuração**, selecione **depurar** na lista suspensa.

1. Selecione **Salvar**.

1. Na caixa de diálogo **publicar** , verifique se **CustomProfile** (ou o nome do perfil que você acabou de criar) aparece e **LastUsedBuildConfiguration** está definido como **depurar**.

1. Selecione **Publicar**.

    ![Publicar no IIS](media/dbg-aspnet-local-iis-select-site.png "Publicar no IIS")

> [!IMPORTANT]
> O modo de depuração reduz consideravelmente o desempenho do seu aplicativo. Para obter o melhor desempenho, defina `debug="false"` no *Web. config* e especifique uma compilação de versão ao implantar um aplicativo de produção ou realizar medidas de desempenho.

## <a name="see-also"></a>Consulte também
- [Depuração do ASP.NET: requisitos do sistema](aspnet-debugging-system-requirements.md)
- [Como executar o processo de trabalho em uma conta de usuário](how-to-run-the-worker-process-under-a-user-account.md)
- [Como localizar o nome do processo ASP.NET](how-to-find-the-name-of-the-aspnet-process.md)
- [Depurar aplicativos Web implantados](debugging-deployed-web-applications.md)
- [Passo a passo: depurando um formulário Web](walkthrough-debugging-a-web-form.md)
- [Como depurar exceções do ASP.NET](how-to-debug-aspnet-exceptions.md)
- [Depurar aplicativos Web: solução de erros e de problemas](debugging-web-applications-errors-and-troubleshooting.md)
