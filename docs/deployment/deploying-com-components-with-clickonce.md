---
title: Implantando componentes COM com ClickOnce | Microsoft Docs
description: Saiba mais sobre as etapas necessárias para implantar aplicativos .NET no ClickOnce que contêm componentes COM herdados.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- registration-free COM deployment
- ClickOnce deployment, COM components
- COM components, deploying
- deploying applications [ClickOnce], COM components
- components, deploying
ms.assetid: 1a4c7f4c-7a41-45f2-9af4-8b1666469b89
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4fc6ef0e4d682f0f712eefc4c139895331c31688
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382917"
---
# <a name="deploy-com-components-with-clickonce"></a>Implantar componentes COM o ClickOnce
A implantação de componentes COM herdados tem sido tradicionalmente uma tarefa difícil. Os componentes precisam ser registrados globalmente e, portanto, podem causar efeitos colaterais indesejáveis entre aplicativos sobrepostos. Essa situação geralmente não é um problema em aplicativos .NET Framework porque os componentes são completamente isolados para um aplicativo ou são compatíveis lado a lado. O Visual Studio permite que você implante componentes COM isolados no sistema operacional Windows XP ou superior.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fornece um mecanismo fácil e seguro para implantar seus aplicativos .NET. No entanto, se seus aplicativos usarem componentes COM herdados, você precisará executar etapas adicionais para implantá-los. Este tópico descreve como implantar componentes COM isolados e referenciar componentes nativos (por exemplo, de Visual Basic 6,0 ou Visual C++).

 Para obter mais informações sobre como implantar componentes COM isolados, consulte [simplificar a implantação de aplicativos com o ClickOnce e o Registration-Free com](https://web.archive.org/web/20050326005413/msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx).

## <a name="registration-free-com"></a>COM sem registro
 O COM livre de registro é uma nova tecnologia para implantar e ativar componentes COM isolados. Ele funciona colocando toda a biblioteca de tipos e as informações de registro do componente que normalmente são instaladas no registro do sistema em um arquivo XML chamado de manifesto, armazenado na mesma pasta que o aplicativo.

 Isolar um componente COM requer que ele seja registrado no computador do desenvolvedor, mas não precisa ser registrado no computador do usuário final. Para isolar um componente COM, tudo o que você precisa fazer é definir sua propriedade **isolada** de referência como **true**. Por padrão, essa propriedade é definida como **false** , indicando que ela deve ser tratada como uma referência com registrada. Se essa propriedade for **true** , ela fará com que um manifesto seja gerado para esse componente no momento da compilação. Ele também faz com que os arquivos correspondentes sejam copiados para a pasta do aplicativo durante a instalação.

 Quando o gerador de manifesto encontra uma referência COM isolada, ele enumera todas as `CoClass` entradas na biblioteca de tipos do componente, correspondendo a cada entrada com seus dados de registro correspondentes e gerando definições de manifesto para todas as classes com no arquivo de biblioteca de tipos.

## <a name="deploy-registration-free-com-components-using-clickonce"></a>Implantar componentes COM sem registro usando o ClickOnce
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] a tecnologia de implantação é adequada para a implantação de componentes COM isolados, porque o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] e o com sem registro exigem que um componente tenha um manifesto para ser implantado.

 Normalmente, o autor do componente deve fornecer um manifesto. No entanto, se não, o Visual Studio é capaz de gerar um manifesto automaticamente para um componente COM. A geração de manifesto é executada durante o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] processo de publicação; para obter mais informações, consulte [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md). Esse recurso também permite aproveitar os componentes herdados que você criou em ambientes de desenvolvimento anteriores, como o Visual Basic 6,0.

 Há duas maneiras de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantar componentes com:

- Use o bootstrapper para implantar seus componentes COM; Isso funciona em todas as plataformas com suporte.

- Use o isolamento de componente nativo (também conhecido como implantação COM livre de registro). No entanto, isso só funcionará em um sistema operacional Windows XP ou superior.

### <a name="example-of-isolating-and-deploying-a-simple-com-component"></a>Exemplo de isolamento e implantação de um componente COM simples
 Para demonstrar a implantação de componente COM sem registro, este exemplo criará um aplicativo baseado no Windows no Visual Basic que faz referência a um componente COM nativo isolado criado usando Visual Basic 6,0 e o implanta usando o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

 Primeiro, você precisará criar o componente COM nativo:

##### <a name="to-create-a-native-com-component"></a>Para criar um componente COM nativo

1. Usando Visual Basic 6,0, no menu **arquivo** , clique em **novo** e em **projeto**.

2. Na caixa de diálogo **novo projeto** , selecione o nó **Visual Basic** e selecione um projeto de **dll ActiveX** . Na caixa **Nome** , digite `VB6Hello`.

    > [!NOTE]
    > Somente os tipos de projeto DLL do ActiveX e de controle ActiveX têm suporte com o COM livre de registro; Não há suporte para os tipos de projeto de documento ActiveX e EXE ActiveX.

3. Em **Gerenciador de soluções** , clique duas vezes em **Class1. vb** para abrir o editor de texto.

4. Em Class1. vb, adicione o seguinte código após o código gerado para o `New` método:

    ```vb
    Public Sub SayHello()
       MsgBox "Message from the VB6Hello COM component"
    End Sub
    ```

5. Crie o componente. No menu **Compilar** , clique em **Solução de Compilação**.

> [!NOTE]
> O COM sem registro oferece suporte somente a DLLs e tipos de projeto de controles COM. Você não pode usar EXEs com com sem registro.

 Agora você pode criar um aplicativo baseado no Windows e adicionar uma referência ao componente COM a ele.

##### <a name="to-create-a-windows-based-application-using-a-com-component"></a>Para criar um aplicativo baseado no Windows usando um componente COM

1. Usando Visual Basic, no menu **arquivo** , clique em **novo** e em **projeto**.

2. Na caixa de diálogo **novo projeto** , selecione o nó **Visual Basic** e selecione **aplicativo do Windows**. Na caixa **Nome** , digite `RegFreeComDemo`.

3. Em **Gerenciador de soluções** , clique no botão **Mostrar todos os arquivos** para exibir as referências do projeto.

4. Clique com o botão direito do mouse no nó **referências** e selecione **Adicionar referência** no menu de contexto.

5. Na caixa de diálogo **Adicionar referência** , clique na guia **procurar** , navegue até VB6Hello.dll e, em seguida, selecione-o.

    Uma referência de **VB6Hello** é exibida na lista de referências.

6. Aponte para a **caixa de ferramentas** , selecione um controle de **botão** e arraste-o para o formulário **Form1** .

7. Na janela **Propriedades** , defina a propriedade **Text** do botão como **Hello**.

8. Clique duas vezes no botão para adicionar o código do manipulador e, no arquivo de código, adicione o código para que o manipulador seja lido da seguinte maneira:

   ```vb
   Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
       Dim VbObj As New VB6Hello.Class1
       VbObj.SayHello()
   End Sub
   ```

9. Executar o aplicativo. No menu **Depurar** , clique em **Iniciar Depuração**.

   Em seguida, você precisa isolar o controle. Cada componente COM que seu aplicativo usa é representado em seu projeto como uma referência COM. Essas referências são visíveis no nó **referências** na janela **Gerenciador de soluções** . (Observe que você pode adicionar referências diretamente usando o comando **Adicionar referência** no menu **projeto** ou indiretamente arrastando um controle ActiveX para o formulário.)

   As etapas a seguir mostram como isolar o componente COM e publicar o aplicativo atualizado que contém o controle isolado:

##### <a name="to-isolate-a-com-component"></a>Para isolar um componente COM

1. Em **Gerenciador de soluções** , no nó **referências** , selecione a referência **VB6Hello** .

2. Na janela **Propriedades** , altere o valor da propriedade **isolada** de **false** para **true**.

3. No menu **Compilar** , clique em **Solução de Compilação**.

   Agora, quando você pressiona F5, o aplicativo funciona conforme o esperado, mas agora ele está sendo executado em COM sem registro. Para provar isso, tente cancelar o registro do componente de VB6Hello.dll e executar RegFreeComDemo1.exe fora do IDE do Visual Studio. Desta vez, quando o botão é clicado, ele ainda funciona. Se você renomear temporariamente o manifesto do aplicativo, ele falhará novamente.

> [!NOTE]
> Você pode simular a ausência de um componente COM Cancelando o registro temporariamente. Abra um prompt de comando, vá para a pasta do sistema digitando `cd /d %windir%\system32` e cancele o registro do componente digitando `regsvr32 /u VB6Hello.dll` . Você pode registrá-lo novamente digitando `regsvr32 VB6Hello.dll` .

 A etapa final é publicar o aplicativo usando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] :

##### <a name="to-publish-an-application-update-with-an-isolated-com-component"></a>Para publicar uma atualização de aplicativo com um componente COM isolado

1. No menu **Compilar** , clique em **Publicar RegFreeComDemo**.

    O Assistente de Publicação será exibido.

2. No assistente de publicação, especifique um local no disco do computador local em que você pode acessar e examinar os arquivos publicados.

3. Clique em **Concluir** para publicar o aplicativo.

   Se você examinar os arquivos publicados, observará que o arquivo Sysmon. ocx está incluído. O controle é totalmente isolado para esse aplicativo, o que significa que, se o computador do usuário final tiver outro aplicativo usando uma versão diferente do controle, ele não poderá interferir nesse aplicativo.

## <a name="reference-native-assemblies"></a>Assemblies nativos de referência
 O Visual Studio dá suporte a referências a assemblies nativos Visual Basic 6,0 ou C++; essas referências são chamadas de referências nativas. Você pode saber se uma referência é nativa verificando se sua propriedade de **tipo de arquivo** está definida como **Native** ou **ActiveX**.

 Para adicionar uma referência nativa, use o comando **Add Reference** e, em seguida, navegue até o manifesto. Alguns componentes colocam o manifesto dentro da DLL. Nesse caso, você pode simplesmente escolher a própria DLL e o Visual Studio a adicionará como uma referência nativa se detectar que o componente contém um manifesto incorporado. O Visual Studio também incluirá automaticamente todos os arquivos dependentes ou assemblies listados no manifesto se eles estiverem na mesma pasta que o componente referenciado.

 O isolamento de controle COM facilita a implantação de componentes COM que ainda não têm manifestos. No entanto, se um componente for fornecido com um manifesto, você poderá fazer referência diretamente ao manifesto. Na verdade, você sempre deve usar o manifesto fornecido pelo autor do componente sempre que possível, em vez de usar a propriedade **isolada** .

## <a name="limitations-of-registration-free-com-component-deployment"></a>Limitações do registro – implantação de componente COM livre
 O COM livre de registro fornece vantagens claras sobre as técnicas de implantação tradicionais. No entanto, há algumas limitações e advertências que também devem ser apontadas. A maior limitação é que ele funciona apenas no Windows XP ou superior. A implementação das alterações requeridas COM do COM registro é a maneira como os componentes são carregados no sistema operacional principal. Infelizmente, não há nenhuma camada de suporte de nível inferior para COM sem registro.

 Nem todo componente é um candidato adequado para COM sem registro. Um componente não será adequado se qualquer uma das seguintes opções for verdadeira:

- O componente é um servidor fora do processo. Não há suporte para os servidores EXE; somente DLLs têm suporte.

- O componente faz parte do sistema operacional, ou é um componente do sistema, como XML, Internet Explorer ou MDAC (Microsoft Data Access Components). Você deve seguir a política de redistribuição do autor do componente; Verifique com seu fornecedor.

- O componente faz parte de um aplicativo, como Microsoft Office. Por exemplo, você não deve tentar isolar o modelo de objeto do Microsoft Excel. Isso faz parte do Office e só pode ser usado em um computador com o produto completo do Office instalado.

- O componente destina-se ao uso como um suplemento ou um snap-in, por exemplo, um suplemento do Office ou um controle em um navegador da Web. Esses componentes normalmente exigem algum tipo de esquema de registro definido pelo ambiente de hospedagem que está além do escopo do próprio manifesto.

- O componente gerencia um dispositivo físico ou virtual para o sistema, por exemplo, um driver de dispositivo para um spooler de impressão.

- O componente é um redistribuível de acesso a dados. Os aplicativos de dados geralmente exigem um redistribuível de acesso a dados separado para serem instalados antes que possam ser executados. Você não deve tentar isolar componentes como o Microsoft ADO Data Control, o Microsoft OLE DB ou o MDAC (Microsoft Data Access Components). Em vez disso, se seu aplicativo usa MDAC ou SQL Server Express, você deve defini-los como pré-requisitos; ver [como: instalar pré-requisitos com um aplicativo ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).

  Em alguns casos, pode ser possível para o desenvolvedor do componente recriá-lo para COM livre de registro. Se isso não for possível, você ainda poderá criar e publicar aplicativos que dependem deles por meio do esquema de registro padrão usando o bootstrapper. Para obter mais informações, consulte [Creating bootstrapper Packages](../deployment/creating-bootstrapper-packages.md).

  Um componente COM só pode ser isolado uma vez por aplicativo. Por exemplo, você não pode isolar o mesmo componente COM de dois projetos de **biblioteca de classes** diferentes que fazem parte do mesmo aplicativo. Isso resultará em um aviso de compilação e o aplicativo não será carregado em tempo de execução. Para evitar esse problema, a Microsoft recomenda que você encapsula os componentes COM em uma única biblioteca de classes.

  Há vários cenários em que o registro COM é necessário na máquina do desenvolvedor, embora a implantação do aplicativo não exija registro. A `Isolated` propriedade requer que o componente com seja registrado no computador do desenvolvedor para gerar automaticamente o manifesto durante a compilação. Não há recursos de captura de registro que invoquem o auto-registro durante a compilação. Além disso, todas as classes não explicitamente definidas na biblioteca de tipos não serão refletidas no manifesto. Ao usar um componente com com um manifesto pré-existente, como uma referência nativa, o componente pode não precisar ser registrado no tempo de desenvolvimento. No entanto, o registro será necessário se o componente for um controle ActiveX e você quiser incluí-lo na **caixa de ferramentas** e no designer de Windows Forms.

## <a name="see-also"></a>Confira também
- [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md)