---
title: Implantação de MSI e VSIX de uma DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 749763a9a2bb742bb3670050010f497c5c15fba4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668592"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>Implantação de uma DSL por MSI e VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode instalar uma linguagem específica de domínio em seu próprio computador ou em outros computadores. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] já deve estar instalado no computador de destino.

## <a name="which"></a>Escolhendo entre a implantação do VSIX e do MSI
 Há dois métodos de implantação de uma linguagem específica de domínio:

|Método|Benefícios|
|------------|--------------|
|VSX (extensão de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)])|Muito fácil de implantar: Copie e execute o arquivo **. vsix** do projeto DslPackage.<br /><br /> Para obter mais informações [, consulte Instalando e desinstalando uma DSL usando o VSX](#Installing).|
|MSI (arquivo do instalador)|-Permite que o usuário abra [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] clicando duas vezes em um arquivo DSL.<br />-Associa um ícone ao tipo de arquivo DSL no computador de destino.<br />-Associa um XSD (esquema XML) ao tipo de arquivo DSL. Isso evita avisos quando o arquivo é carregado em [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].<br /><br /> Você deve adicionar um projeto de instalação à sua solução para criar um MSI.<br /><br /> Para obter mais informações, consulte [implantando uma DSL usando um arquivo MSI](#msi).|

## <a name="Installing"></a>Instalando e desinstalando uma DSL usando o VSX
 Quando o DSL é instalado por esse método, o usuário pode abrir um arquivo DSL no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], mas o arquivo não pode ser aberto no Windows Explorer.

#### <a name="to-install-a-dsl-by-using-the-vsx"></a>Para instalar uma DSL usando o VSX

1. Em seu computador, localize o arquivo **. vsix** criado por seu projeto de pacote DSL.

    1. No **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **DslPackage** e clique em **abrir pasta no Windows Explorer**.

    2. Localize o arquivo **bin \\ \* \\** _seuprojeto_ **. DslPackage. vsix**

2. Copie o arquivo **. vsix** para o computador de destino no qual você deseja instalar a DSL. Este pode ser seu próprio computador ou outro.

    - O computador de destino deve ter uma das edições do [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] que dá suporte a DSLs em tempo de execução. Para obter mais informações, consulte [supported Visual Studio Editions for visualization & Modeling SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

    - O computador de destino deve ter uma das edições do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] especificado em **DslPackage\source.Extensions.manifest**.

3. No computador de destino, clique duas vezes no arquivo **. vsix** .

     O **instalador de extensão do Visual Studio** é aberto e instala a extensão.

4. Inicie ou reinicie o [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

5. Para testar a DSL, use [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para criar um novo arquivo que tenha a extensão que você definiu para a sua DSL.

#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Para desinstalar uma DSL que foi instalada usando o VSX

1. No menu **ferramentas** , clique em **Gerenciador de extensões**.

2. Expanda **extensões instaladas**.

3. Selecione a extensão na qual a DSL está definida e clique em **desinstalar**.

   Raramente, uma extensão defeituosa não carrega e cria um relatório na janela de erro, mas não aparece no Gerenciador de extensões. Nesse caso, você pode remover a extensão excluindo o arquivo de:

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**

## <a name="msi"></a>Implantando uma DSL em um MSI
 Ao definir um arquivo MSI (Windows Installer) para sua DSL, você pode permitir que os usuários abram arquivos DSL no Windows Explorer. Você também pode associar um ícone e uma breve descrição à sua extensão de nome de arquivo. Além disso, o MSI pode instalar um XSD que pode ser usado para validar arquivos DSL. Se desejar, você pode adicionar outros componentes ao MSI que serão instalados ao mesmo tempo.

 Para obter mais informações sobre arquivos MSI e outras opções de implantação, consulte [Implantando aplicativos, serviços e componentes](../deployment/deploying-applications-services-and-components.md).

 Para criar um MSI, você adiciona um projeto de instalação à sua solução de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. O método mais fácil de criar um projeto de instalação é usar o modelo CreateMsiSetupProject.tt, que pode ser baixado do [site do VMSDK](http://go.microsoft.com/fwlink/?LinkID=186128).

#### <a name="to-deploy-a-dsl-in-an-msi"></a>Para implantar uma DSL em um MSI

1. Defina `InstalledByMsi` no manifesto de extensão. Isso impede que o VSX seja instalado e desinstalado, exceto pelo MSI. Isso será importante se você incluir outros componentes no MSI.

   1. Abrir DslPackage\source.extension.tt

   2. Insira a linha a seguir antes de `<SupportedProducts>`:

       ```
       <InstalledByMsi>true</InstalledByMsi>
       ```

2. Crie ou edite um ícone que representará sua DSL no Windows Explorer. Por exemplo, edite **DslPackage\Resources\File.ico**

3. Verifique se os seguintes atributos de sua DSL estão corretos:

   - No Gerenciador de DSL, clique no nó raiz e, em janela Propriedades, examine:

       - Descrição

       - Version

   - Clique no nó do **Editor** e, na janela Propriedades, clique em **ícone**. Defina o valor para fazer referência a um arquivo de ícone em **DslPackage\Resources**, como **File. ico**

   - No menu **Compilar** , abra **Configuration Manager**e selecione a configuração que você deseja compilar, como **liberar** ou **depurar**.

4. Acesse o [SDK de visualização e modelagem Home Page](http://go.microsoft.com/fwlink/?LinkID=186128)e, na guia **Downloads** , baixe **CreateMsiSetupProject.tt**.

5. Adicione **CreateMsiSetupProject.tt** ao seu projeto DSL.

    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] criará um arquivo chamado **CreateMsiSetupProject. vdproj**.

6. No Windows Explorer, copie DSL \\ *. vdproj para uma nova pasta chamada setup.

    (Se desejar, agora você pode excluir CreateMsiSetupProject.tt de seu projeto DSL.)

7. Em **Gerenciador de soluções**, adicione **a instalação \\ \*. vdproj** como um projeto existente.

8. No menu **projeto** , clique em **dependências do projeto**.

    Na caixa de diálogo **dependências do projeto** , selecione o projeto de instalação.

    Selecione a caixa ao lado de **DslPackage**.

9. Recompile a solução.

10. No Windows Explorer, localize o arquivo MSI compilado em seu projeto de instalação.

     Copie o arquivo MSI em um computador no qual você deseja instalar o DSL. Clique duas vezes no arquivo MSI. O instalador é executado.

11. No computador de destino, crie um novo arquivo que tenha a extensão de arquivo de sua DSL. Verifique se:

    - No modo de exibição de lista do Windows Explorer, o arquivo aparece com o ícone e a descrição que você definiu.

    - Quando você clica duas vezes no arquivo, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] é iniciado e abre o arquivo DSL em seu editor DSL.

    Se preferir, você pode criar o projeto de instalação manualmente, em vez de usar o modelo de texto. Para obter uma explicação que inclui esse procedimento, consulte o capítulo 5 do [laboratório de visualização e do SDK de modelagem](http://go.microsoft.com/fwlink/?LinkId=208878).

#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>Para desinstalar uma DSL que foi instalada a partir de um MSI

1. No Windows, abra o painel de controle **programas e recursos** .

2. Desinstale a DSL.

3. Reinicie o Visual Studio.
