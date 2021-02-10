---
title: Implantando uma solução do VSTO usando o Windows Installer
description: Saiba como implantar um suplemento do VSTO (Microsoft Visual Studio Tools for Office) ou uma solução em nível de documento usando um projeto Instalador do Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 08/18/2010
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, setup project
- Office development in Visual Studio, MSI
- deploying applications [Office development in Visual Studio], setup project
- deploying applications [Office development in Visual Studio], MSI
- ClickOnce deployment [Office development in Visual Studio], MSI
- publishing Office solutions [Office development in Visual Studio], setup project
- Office applications [Office development in Visual Studio], MSI
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 75c2d97e8cd30bb3cf5605d50e65a68513590647
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939364"
---
# <a name="deploying-a-vsto-solution-using-windows-installer"></a>Implantando uma solução do VSTO usando o Windows Installer

## <a name="summary"></a>Resumo

Saiba como implantar um suplemento do VSTO (Microsoft Visual Studio Tools for Office) ou uma solução em nível de documento usando um projeto Instalador do Visual Studio.

Wouter van Vugt, advogado de código

Ted Pattison, grupo Ted Pattison

Este artigo foi atualizado pela Microsoft com permissão dos autores originais.

**Aplica-se a:** Ferramentas do Visual Studio para Office, Microsoft Office Microsoft Visual Studio.

## <a name="overview"></a>Visão geral

Você pode desenvolver uma solução VSTO e implantar a solução usando um pacote Windows Installer. Esta discussão inclui etapas para implantar um suplemento simples do Office.

## <a name="deployment-methods"></a>Métodos de implantação

O ClickOnce pode ser facilmente usado para criar configurações para seus suplementos e soluções. No entanto, ele não pode instalar suplementos que exigem privilégios administrativos, como suplementos de nível de máquina.

Suplementos que exigem privilégios administrativos podem ser instalados usando Windows Installer, mas exigem mais esforço para criar a configuração.

Para obter uma visão geral de como implantar uma solução do VSTO usando o ClickOnce, consulte [implantar uma solução do Office usando o ClickOnce](deploying-an-office-solution-by-using-clickonce.md).

## <a name="deploying-office-solutions-that-target-the-vsto-runtime"></a>Implantando soluções do Office direcionadas ao tempo de execução do VSTO

Os pacotes ClickOnce e Windows Installer precisam fazer as mesmas tarefas rudimentares ao instalar uma solução do Office.

1. Instale os componentes de pré-requisito no computador do usuário.
2. Implante os componentes específicos para a solução.
3. Para suplementos, crie entradas do registro.
4. Confie na solução para permitir que ela seja executada.

### <a name="required-prerequisite-components-on-the-target-computer"></a>Componentes de pré-requisito necessários no computador de destino

Aqui está a lista de softwares que devem ser instalados no computador para executar soluções do VSTO:

- Microsoft Office 2010 ou mais recente.
- O Microsoft .NET Framework 4 ou mais recente.
- Microsoft Visual Studio 2010 Tools for Office Runtime.
  O tempo de execução fornece um ambiente que gerencia suplementos e soluções de nível de documento. Uma versão do tempo de execução é fornecida com Microsoft Office, mas talvez você queira redistribuir uma versão específica com seu suplemento.
- Os assemblies de interoperabilidade primários para Microsoft Office, se você não estiver usando tipos de interoperabilidade inseridos.
- Quaisquer assemblies de utilitários referenciados por projetos.

### <a name="specific-components-for-the-solution"></a>Componentes específicos para a solução

O pacote do instalador deve instalar esses componentes no computador do usuário:

- O documento Microsoft Office, se você criar uma solução em nível de documento.
- O assembly de personalização e quaisquer assemblies exigidos por ele.
- Componentes adicionais, como arquivos de configuração.
- O manifesto do aplicativo (. manifest).
- O manifesto de implantação (. vsto).

### <a name="registry-entries-for-add-ins"></a>Entradas de registro para suplementos

Microsoft Office usa entradas de registro para localizar e carregar suplementos. Essas entradas de registro devem ser criadas como parte do processo de implantação. Para obter mais informações sobre essas entradas de registro, consulte [entradas de registro para suplementos do VSTO](registry-entries-for-vsto-add-ins.md).

Os suplementos do Outlook que exibem regiões de formulário personalizadas exigem entradas de registro adicionais que permitem que as regiões de formulário sejam identificadas. Para obter mais informações sobre entradas do registro, consulte [entradas do registro para regiões de formulário do Outlook](registry-entries-for-vsto-add-ins.md#OutlookEntries).

Soluções de nível de documento não exigem entradas de registro. Em vez disso, as propriedades dentro do documento são usadas para localizar a personalização. Para obter mais informações sobre essas propriedades, consulte [visão geral de propriedades de documento personalizadas](custom-document-properties-overview.md).

### <a name="trusting-the-vsto-solution"></a>Confiando na solução VSTO

Para que uma personalização seja executada, uma solução deve ser confiável para a máquina. O suplemento pode ser confiável assinando o manifesto com um certificado, criando uma relação de confiança com uma lista de inclusão ou instalando-a em um local confiável no computador.

Para obter mais informações sobre como obter um certificado para assinatura, consulte [implantação do ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md). Para obter mais informações sobre soluções de confiança, consulte [confiando em soluções de escritório usando listas de inclusão](trusting-office-solutions-by-using-inclusion-lists.md). Você pode adicionar uma entrada de lista de inclusão com uma ação personalizada no arquivo Windows Installer. Para obter mais informações sobre como habilitar a lista de inclusão, consulte [como: configurar a segurança da lista de inclusão](how-to-configure-inclusion-list-security.md).

Se nenhuma opção for usada, um prompt de confiança será exibido para o usuário para permitir que eles decidam se devem confiar na solução.

Para obter mais informações sobre segurança relacionada a soluções de nível de documento, consulte [concedendo confiança a documentos](granting-trust-to-documents.md).

## <a name="creating-a-basic-installer"></a>Criando um instalador básico

Os modelos de projeto de instalação e implantação estão incluídos com a extensão de [projetos do Microsoft Visual Studio Installer](https://marketplace.visualstudio.com/items?itemName=visualstudioclient.MicrosoftVisualStudio2017InstallerProjects) que está disponível para download.

Para criar um instalador para uma solução do Office, essas tarefas devem ser realizadas:

- Adicione os componentes da solução do Office que será implantada.
- Para suplementos no nível do aplicativo, configure as chaves do registro.
- Configure os componentes de pré-requisito para que eles possam ser instalados nos computadores dos usuários finais.
- Configure as condições de inicialização para verificar se os componentes de pré-requisito necessários estão disponíveis. As condições de inicialização podem ser usadas para bloquear a instalação se todos os pré-requisitos necessários não estiverem instalados.

A primeira etapa é criar o projeto de instalação.

### <a name="to-create-the-addin-setup-project"></a>Para criar o projeto de configuração de suplemento

1. Abra o projeto de suplemento do Office que você deseja implantar. Para este exemplo, estamos usando um suplemento do Excel chamado ExcelAddIn.
2. Com o projeto do Office aberto, no menu **arquivo** , expanda **Adicionar** e clique em **novo projeto** para adicionar um novo projeto.
::: moniker range="=vs-2017"
3. Na caixa de diálogo **Adicionar novo projeto** , expanda **outros tipos de projeto** no painel **tipos de projeto** , expanda **instalação e implantação** e, em seguida, selecione **instalador do Visual Studio**.
4. No painel **modelos** , selecione **Configurar projeto** no grupo modelos **instalados do Visual Studio** .
::: moniker-end
::: moniker range="=vs-2019"
3. Na caixa de diálogo **Adicionar um novo projeto** , selecione o modelo de **projeto de instalação** .
4. Clique em **Próximo**.
::: moniker-end

5. Na caixa **nome** , digite **OfficeAddInSetup**.
::: moniker range="=vs-2017"
6. Clique em **abrir** para criar o novo projeto de instalação.
::: moniker-end
::: moniker range="=vs-2019"
6. Clique em **criar** para criar o novo projeto de instalação.
::: moniker-end

O Visual Studio abre o explorador do sistema de arquivos para o novo projeto de instalação. O Gerenciador de sistema de arquivos permite que você adicione arquivos ao projeto de instalação.

   ![Captura de tela do explorador do sistema de arquivos para o projeto de instalação](media/setup-project-figure-1.png)

   **Figura 1: explorador do sistema de arquivos para o projeto de instalação**

O projeto de instalação precisa implantar o ExcelAddIn. Você pode configurar o projeto de instalação para essa tarefa adicionando a saída do projeto ExcelAddIn ao projeto de instalação.

### <a name="to-add-the-exceladdin-project-output"></a>Para adicionar a saída do projeto ExcelAddIn

1. Na **Gerenciador de soluções**, clique com o botão direito do mouse em **OfficeAddInSetup**, clique em **Adicionar** e, em seguida, em **saída do projeto**.
2. Na caixa de diálogo **Adicionar grupo de saída do projeto** , selecione o **ExcelAddIn** na lista de projetos e a **saída primária**.
3. Clique em **OK** para adicionar a saída do projeto ao projeto de instalação.

    ![Captura de tela da caixa de diálogo configuração do projeto Adicionar grupo de saída do projeto](media/setup-project-figure-2.png)

    **Figura 2: caixa de diálogo de Adicionar grupo de saída do projeto de instalação**

O projeto de instalação precisa implantar o manifesto de implantação e o manifesto do aplicativo. Adicione esses dois arquivos ao projeto de instalação como arquivos autônomos da pasta de saída do projeto ExcelAddIn.

### <a name="to-add-the-deployment-and-application-manifests"></a>Para adicionar os manifestos de implantação e de aplicativo

1. Na **Gerenciador de soluções**, clique com o botão direito do mouse em **OfficeAddInSetup**, clique em **Adicionar** e clique em **arquivo**.
2. Na caixa de diálogo **Adicionar arquivos** , navegue até o diretório de saída **ExcelAddIn** . Normalmente, o diretório de saída é a subpasta **bin \\ Release** do diretório raiz do projeto, dependendo da configuração da compilação selecionada.
3. Selecione os arquivos **ExcelAddIn. vsto** e **ExcelAddIn.dll. manifest** e clique em **abrir** para adicionar esses dois arquivos ao projeto de instalação.

    ![Captura de tela dos manifestos de aplicativo e implantação no Gerenciador de Soluções](media/setup-project-figure-3.jpg)

    **Figura 3: manifestos de aplicativo e implantação para o suplemento no Gerenciador de Soluções**

A referência ao ExcelAddIn inclui todos os componentes que o ExcelAddIn exige. Esses componentes devem ser excluídos e implantados usando pacotes de pré-requisito para permitir que eles sejam registrados corretamente. Além disso, os termos de licença de software devem ser exibidos e aceitos antes do início da instalação.

### <a name="to-exclude-the-exceladdin-project-dependencies"></a>Para excluir as dependências do projeto ExcelAddIn

1. No **Gerenciador de soluções**, no nó **OfficeAddInSetup** , selecione todos os itens de dependência abaixo do item **dependências detectadas** , exceto para **Microsoft .NET Framework** ou qualquer assembly que termine com **\*.Utilities.dll**. Os assemblies de utilitários devem ser implantados junto com seu aplicativo.
2. Clique com o botão direito do mouse no grupo e selecione **Propriedades**.
3. Na janela **Propriedades** , altere a propriedade **Exclude** para **true** para excluir os assemblies dependentes do projeto de instalação. Certifique-se de não excluir nenhum assembly de utilitários.

    ![Captura de tela de Gerenciador de Soluções mostrando as dependências a serem excluídas](media/setup-project-figure-4.jpg)

    **Figura 4: excluindo dependências**

Você pode configurar seu pacote de Windows Installer para instalar os componentes de pré-requisito adicionando um programa de instalação, também conhecido como bootstrapper. Este programa de instalação pode instalar os componentes de pré-requisito, um processo chamado inicialização.

Para o **ExcelAddIn**, esses pré-requisitos devem ser instalados para que o suplemento possa ser executado corretamente:

- A versão do Microsoft .NET Framework para a qual a solução do Office se destina.
- Microsoft Visual Studio 2010 Tools para Office Runtime.

Para configurar componentes dependentes como pré-requisitos

1. Na **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **OfficeAddInSetup** e selecione **Propriedades**.
2. A caixa de diálogo **páginas de propriedades do OfficeAddInSetup** é exibida.
3. Clique no botão **pré-requisitos** .
4. Na caixa de diálogo pré-requisitos, selecione a versão correta do .NET Framework e o Microsoft Visual Studio ferramentas para tempo de execução do Office.

    ![Captura de tela da caixa de diálogo pré-requisitos](media/setup-project-figure-5.png)

    **Figura 5: caixa de diálogo pré-requisitos**

    > [!NOTE]
    >Alguns dos pacotes de pré-requisito configurados no seu projeto de instalação do Visual Studio dependem da configuração de compilação selecionada. Você deve selecionar os componentes de pré-requisito corretos para cada configuração de compilação que você usa.

Microsoft Office localiza suplementos usando chaves do registro. As chaves no hive HKEY \_ Current \_ User são usadas para registrar o suplemento para cada usuário individual. As chaves no hive do \_ computador local hKey \_ são usadas para registrar o suplemento para todos os usuários do computador. Para obter mais informações sobre chaves do registro, consulte [entradas do registro para suplementos do VSTO](registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-the-registry"></a>Para configurar o registro

1. Na **Gerenciador de soluções**, clique com o botão direito do mouse em **OfficeAddInSetup**.
2. Expandir **exibição**.
3. Clique em **registro** para abrir a janela do editor do registro.
4. No editor **do registro (OfficeAddInSetup)** , expanda **HKEY \_ local \_ Machine** e, em seguida, **software**.
5. Excluir o **\[ fabricante \]**? chave encontrada em **HKEY \_ local \_ Machine \\ software**.
6. Expanda **HKEY \_ Current \_ User** e, em seguida, **software**.
7. Exclua a chave do **\[ fabricante \]** encontrada em **HKEY \_ atual \_ \\ software do usuário**.
8. Para adicionar chaves do registro para a instalação do suplemento, clique com o botão direito do mouse na chave do **hive do usuário/computador** , selecione **nova chave**. Use o **software** de texto para o nome da nova chave. Clique com o botão direito do mouse na chave de **software** criada recentemente e crie uma nova chave com o texto **Microsoft**.
9. Use um processo semelhante para criar a hierarquia de chave inteira necessária para o registro do suplemento:

    **Software hive do usuário/computador \\ \\ Microsoft \\ Office \\ Excel \\ AddIns \\ SampleCompany. ExcelAddIn**

    O nome da empresa é geralmente usado como um prefixo para o nome do suplemento para fornecer exclusividade.

10. Clique com o botão direito do mouse na chave **SampleCompany. ExcelAddIn** , selecione **novo** e clique em **valor da cadeia de caracteres**. Use a **Descrição** de texto para o nome.
11. Use esta etapa para adicionar mais três valores:
    - **FriendlyName** do tipo **cadeia de caracteres**
    - **LoadBehavior** do tipo **DWORD**
    - **Manifesto** do tipo **cadeia de caracteres**

12. Clique com o botão direito do mouse no valor da **Descrição** no editor do registro e clique em **janela de propriedades**. Na **janela Propriedades**, insira **suplemento de demonstração do Excel** para a propriedade valor.
13. Selecione a chave **FriendlyName** no editor do registro. Na **janela Propriedades**, altere a propriedade **valor** para **suplemento de demonstração do Excel**.
14. Selecione a chave **LoadBehavior** no editor do registro. Na **janela Propriedades**, altere a propriedade **valor** para **3.** O valor 3 para o LoadBehavior indica que o suplemento deve ser carregado na inicialização do aplicativo host. Para obter mais informações sobre o comportamento de carregamento, consulte [entradas do registro para suplementos do VSTO](registry-entries-for-vsto-add-ins.md).

15. Selecione a chave do **manifesto** no editor do registro. Na **janela Propriedades**, altere a propriedade **valor** para **arquivo:///[TARGETDIR] ExcelAddIn. vsto | vstolocal**

    ![Captura de tela do editor do registro](media/setup-project-figure-6.png)

    **Figura 6: Configurando chaves do registro**

      O tempo de execução do VSTO usa essa chave do registro para localizar o manifesto de implantação. A macro [TARGETDIR] será substituída pela pasta em que o suplemento está instalado. A macro incluirá o caractere \ à direita, portanto, o nome do arquivo do manifesto de implantação deve ser ExcelAddIn. vsto sem o caractere \.
      O sufixo **vstolocal** , informa ao tempo de execução do VSTO que o suplemento deve carregar desse local em vez do cache do ClickOnce. A remoção desse sufixo fará com que o tempo de execução Copie a personalização no cache do ClickOnce.

   >[!WARNING]
   >Você deve ter muito cuidado com o editor do registro no Visual Studio. Por exemplo, se você definir acidentalmente DeleteAtUninstall para a chave incorreta, poderá excluir uma parte ativa do registro, deixando o computador do usuário em um estado inconsistente, ou ainda pior, desfeito.

as versões de 64 bits do Office usarão o hive do registro de 64 bits para procurar suplementos. Para registrar suplementos no hive do registro de 64 bits, a plataforma de destino do projeto de instalação deve ser definida como somente 64 bits.

1. Selecione o projeto **OfficeAddInSetup** no Gerenciador de soluções.
2. Vá para a janela **Propriedades** e defina a propriedade **TargetPlatform** como **x64**.

A instalação de um suplemento para as versões de 32 bits e 64 bits do Office exigirá que você crie dois pacotes MSI separados. Um para 32 bits e outro para 64 bits.

  ![Captura de tela da janela Propriedades mostrando a plataforma de destino para o registro de suplementos com o Office de 64 bits](media/setup-project-figure-7.jpg)

  **Figura 7: plataforma de destino para o registro de suplementos com o Office de 64 bits**

Se o pacote MSI for usado para instalar o suplemento ou a solução, ele poderá ser instalado sem que os pré-requisitos necessários sejam instalados. Você pode usar as condições de inicialização no MSI para impedir que o suplemento seja instalado se os pré-requisitos não estiverem instalados.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime"></a>Configurar uma condição de inicialização para detectar o tempo de execução do VSTO

1. Na **Gerenciador de soluções**, clique com o botão direito do mouse em **OfficeAddInSetup**.
2. Expandir **exibição**.
3. Clique em **condições de inicialização**.
4. No editor de **condições de inicialização (OfficeAddInSetup)** , clique com o botão direito do mouse em **requisitos no computador de destino** e clique em **Adicionar condição de inicialização do registro**. Esse critério de pesquisa pode pesquisar o registro em busca de uma chave instalada pelo tempo de execução do VSTO. O valor da chave estará disponível para as várias partes do instalador por meio de uma propriedade nomeada. A condição de inicialização usa a propriedade definida pelo critério de pesquisa para verificar um determinado valor.
5. No editor de **condições de inicialização (OfficeAddInSetup)** , selecione o critério de pesquisa **do RegistryEntry1** de pesquisa, clique com o botão direito do mouse na condição e selecione **janela de propriedades**.

6. Na janela **Propriedades** , defina estas propriedades:
   1. Defina o valor de **(Name)** para **Pesquisar o tempo de execução do VSTO 2010**.
   2. Altere o valor da **Propriedade** para **VSTORUNTIMEREDIST**.
   3. Defina o valor de **RegKey** para **software \\ Microsoft \\ VSTO Runtime Setup \\ v4R**
   4. Deixe a propriedade **raiz** definida como **vsdrrHKLM**.
   5. Altere a propriedade **Value** para **version**.

7. No editor de **condições de inicialização (OfficeAddInSetup)** , selecione a condição de inicialização **condição1** , clique com o botão direito do mouse na condição e selecione **janela de propriedades**.
8. No janela Propriedades, defina estas propriedades:
   1. Defina o **(Name)** para **verificar a disponibilidade de tempo de execução do VSTO 2010**.
   2. Altere o valor da **condição** para **VSTORUNTIMEREDIST \> = "10.0.30319"**
   3. Deixe a propriedade **InstallUrl** em branco.
   4. Definir a **mensagem** para **o tempo de execução das ferramentas do Visual Studio 2010 para Office não está instalada. Execute Setup.exe para instalar o suplemento**.

        ![Captura de tela da janela Propriedades da condição de inicialização verificar disponibilidade de tempo de execução](media/setup-project-figure-8.jpg)

        **Figura 8: janela Propriedades para a condição de inicialização verificar disponibilidade de tempo de execução**

 A condição de inicialização acima verifica explicitamente a presença do tempo de execução do VSTO quando ele é instalado pelo pacote de bootstrapper.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime-installed-by-office"></a>Configurar uma condição de inicialização para detectar o tempo de execução do VSTO instalado pelo Office

1. No editor de **condições de inicialização (OfficeAddInSetup)** , clique com o botão direito do mouse em **Pesquisar computador de destino** e clique em **Adicionar pesquisa de registro**.
2. Selecione o critério de pesquisa **de pesquisa de RegistryEntry1** , clique com o botão direito do mouse na condição e selecione **janela de propriedades**.
3. Na janela **Propriedades** , defina estas propriedades:
    1. Defina o valor de **(Name)** para **Pesquisar o tempo de execução do VSTO do Office**.
    2. Altere o valor da **Propriedade** para **OfficeRuntime**.
    3. Defina o valor de **RegKey** para **software \\ Microsoft \\ VSTO Runtime Setup \\ v4**.
    4. Deixe a propriedade **raiz** definida como **vsdrrHKLM**.
    5. Altere a propriedade **Value** para **version**.

4. No editor de **condições de inicialização (OfficeAddInSetup)** , selecione a condição de inicialização **verificar a disponibilidade de tempo de execução do VSTO 2010** definida anteriormente, clique com o botão direito do mouse na condição e selecione **janela de propriedades**.

5. Altere o valor da propriedade **Condition** para **VSTORUNTIMEREDIST \> = "10.0.30319" ou OFFICERUNTIME \> = "10.0.21022"**. Os números de versão talvez sejam diferentes para você dependendo das versões do tempo de execução que seu suplemento requer.

    ![Captura de tela das janelas de propriedades para a condição de inicialização](media/setup-project-figure-9.jpg)
  
    **Figura 9: janelas de propriedades para verificar a disponibilidade do tempo de execução por meio do Redist ou da condição de inicialização do Office**

Se um suplemento tiver um destino .NET Framework 4 ou mais recente, os tipos dentro dos assemblies de interoperabilidade primários (PIA) que são referenciados poderão ser inseridos no assembly do VSTO.

Para verificar se os tipos de interoperabilidade serão inseridos no seu suplemento executando as seguintes etapas:

1. Expanda o nó referências no Gerenciador de Soluções
2. Selecione uma das referências de PIA, por exemplo, **Office**.
3. Exiba as janelas de propriedades atingindo F4 ou selecionando Propriedades no menu de contexto assemblies.
4. Verifique o valor da propriedade **inserir tipos de interoperabilidade**.

Se o valor for definido como **true**, os tipos serão inseridos e você poderá pular para a seção [**para criar o projeto de instalação**](#to-build-the-setup-project) .

Para obter mais informações, consulte [equivalências de tipo e tipos de interoperabilidade inseridos](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types)

### <a name="to-configure-launch-conditions-to-detect-that-for-office-pias"></a>Para configurar condições de inicialização para detectar os PIAs do Office

1. No editor de **condições de inicialização (OfficeAddInSetup)** , clique com o botão direito do mouse em **requisitos no computador de destino** e **clique em Adicionar Windows Installer condição de inicialização**. Essa condição de inicialização procura um PIA do Office pesquisando a ID do componente específico.
2. Clique com o botão direito do mouse em **Pesquisar por Component1** e clique em **janela de propriedades** para mostrar as propriedades da condição de inicialização.
3. Na **janela Propriedades**, defina estas propriedades:

    1. Altere o valor da propriedade **(Name)** para **Pesquisar o pia compartilhado do Office**
    2. Altere o valor da ID **do componente para o** componente do Office que você está usando. Você pode encontrar a lista de IDs de componentes na tabela abaixo, por exemplo **{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}**.
    3. Altere o valor da propriedade **Property** para **HASSHAREDPIA**.

4. No editor de **condições de inicialização (OfficeAddInSetup)** , clique com o botão direito do mouse em **condição1** e clique em **janela de propriedades** para mostrar as propriedades da condição de inicialização.

5. Altere essas propriedades de **condição1**:

    1. Altere o **(nome)** para **verificar a disponibilidade do pia compartilhado do Office**.
    2. Altere a **condição** para **HASSHAREDPIA**.
    3. Deixe **InstallUrl** em branco.
    4. Altere a **mensagem** para **um componente necessário para interagir com o Excel não está disponível. Execute setup.exe**.

    ![Captura de tela da janela Propriedades para verificar a condição de inicialização do PIA compartilhado do Office](media/setup-project-figure-10.jpg)
  
    **Figura 10: janela Propriedades para a condição de inicialização verificar o PIA compartilhado do Office**

### <a name="component-ids-of-the-primary-interop-assemblies-for-microsoft-office"></a>IDs de componente dos assemblies de interoperabilidade primários para Microsoft Office

|Assembly de interoperabilidade primária|Office 2010|Office 2013|Office 2013 (64 bits)|Office 2016|Office 2016 (64 bits)|
|------------------------|------------------------|------------------------|------------------------|------------------------|------------------------|
|Excel|{EA7564AC-C67D-4868-BE5C-26E4FC2223FF}|{C8A65ABE-3270-4FD7-B854-50C8082C8F39}|{E3BD1151-B9CA-4D45-A77E-51A6E0ED322A}|C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|{C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|
|InfoPath|{4153F732-D670-4E44-8AB7-500F2B576BDA}|{0F825A16-25B2-4771-A497-FC8AF3B355D8}|{C5BBD36E-B320-47EF-A512-556B99CB7E41}|-|-|
|Outlook|{1D844339-3DAE-413E-BC13-62D6A52816B2}|{F9F828D5-9F0B-46F9-9E3E-9C59F3C5E136}|{7824A03F-28CC-4371-BC54-93D15EFC1E7F}|{7C6D92EF-7B45-46E5-8670-819663220E4E}|{7C6D92EF-7B45-46E5-8670-819663220E4E}|
|PowerPoint|{EECBA6B8-3A62-44AD-99EB-8666265466F9}|{813139AD-6DAB-4DDD-8C6D-0CA30D073B41}|{05758318-BCFD-4288-AD8D-81185841C235}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|
|Visio|{3EA123B5-6316-452E-9D51-A489E06E2347}|{C1713368-12A8-41F1-ACA1-934B01AD6EEB}|{2CC0B221-22D2-4C15-A9FB-DE818E51AF75}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|
|Word|{8B74A499-37F8-4DEA-B5A0-D72FC501CEFA}|{9FE736B7-B1EE-410C-8D07-082891C3DAC8}|{13C07AF5-B206-4A48-BB5B-B8022333E3CA}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|
|Microsoft Forms 2,0|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{A5A30117-2D2A-4C5C-B3C8-8897AC32C2AC}|-|-|
|Microsoft Graph|{011B9112-EBB1-4A6C-86CB-C2FDC9EA7B0E}|{52DA4B37-B8EB-4B7F-89C1-824654CE4C70}|{24706F33-F0CE-4EB4-BC91-9E935394F510}|-|-|
|Marca inteligente|{7102C98C-EF47-4F04-A227-FE33650BF954}|{487A7921-EB3A-4262-BB5B-A5736B732486}|{74EFC1F9-747D-4867-B951-EFCF29F51AF7}|-|-|
|Compartilhado do Office|{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}|{6A174BDB-0049-4D1C-86EF-3114CB0C4C4E}|{76601EBB-44A7-49EE-8DE3-7B7B9D7EBB05}|{625F5772-C1B3-497E-8ABE-7254EDB00506}|{625F5772-C1B3-497E-8ABE-7254EDB00506}|
|Project|{957A4EC0-E67B-4E86-A383-6AF7270B216A}|{1C50E422-24FA-44A9-A120-E88280C8C341}|{706D7F44-8231-489D-9B25-3025ADE9F114}|{107BCD9A-F1DC-4004-A444-33706FC10058}|{107BCD9A-F1DC-4004-A444-33706FC10058}|

  ![Captura de tela das condições de lançamento final](media/setup-project-figure-11.jpg)

  **Figura 11: condições de inicialização final**

Você pode refinar ainda mais as condições de inicialização para a instalação do ExcelAddIn. Por exemplo, talvez seja útil verificar se o aplicativo do Office de destino real está instalado.

### <a name="to-build-the-setup-project"></a>Para compilar o projeto de instalação

1. Na **Gerenciador de soluções**, clique com o botão direito do mouse no projeto **OfficeAddInSetup** e clique em **Compilar**.
2. Usando o **Windows Explorer**, navegue até o diretório de saída do projeto **OfficeAddInSetup** e vá para a pasta versão ou depuração, dependendo da configuração da compilação selecionada. Copie todos os arquivos da pasta para um local que os usuários possam acessar.

Para testar a configuração do ExcelAddIn

1. Navegue até o local onde você copiou **OfficeAddInSetup** para.
2. Clique duas vezes no arquivo de setup.exe para instalar o suplemento **OfficeAddInSetup** . Aceite os termos de licença de software que aparecem e conclua o assistente de instalação para instalar o suplemento no computador do usuário.

A solução do Office Excel deve ser instalada e executada a partir do local especificado durante a instalação.

## <a name="additional-requirements-for-document-level-solutions"></a>Requisitos adicionais para soluções de nível de documento

A implantação de soluções em nível de documento requer algumas etapas de configuração diferentes no projeto de instalação Windows Installer.

Aqui está uma lista das etapas básicas necessárias para implantar uma solução em nível de documento:

- Crie o projeto de instalação do Visual Studio.
- Adicione a saída primária de sua solução em nível de documento. A saída primária também inclui o documento Microsoft Office.
- Adicione os manifestos de implantação e de aplicativo como arquivos flexíveis.
- Exclua os componentes dependentes do pacote do instalador (exceto para todos os assemblies de utilitários).
- Configure os pacotes de pré-requisito.
- Configurar condições de inicialização.
- Crie o projeto de instalação e copie os resultados para o local de implantação.
- Implante a solução em nível de documento no computador do usuário executando a instalação.
- Atualize as propriedades do documento personalizado, se necessário.

### <a name="changing-the-location-of-the-deployed-document"></a>Alterando o local do documento implantado

As propriedades dentro de um documento do Office são usadas para localizar soluções de nível de documento. Se o documento for instalado na mesma pasta que o assembly do VSTO, nenhuma alteração será necessária. No entanto, se ele estiver instalado em uma pasta diferente, essas propriedades precisarão ser atualizadas durante a instalação.

Para obter mais informações sobre essas propriedades de documento, consulte [visão geral de propriedades de documento personalizadas](custom-document-properties-overview.md).

Para alterar essas propriedades, você precisa usar uma ação personalizada durante a instalação.

O exemplo a seguir usa uma solução de nível de documento chamada ExcelWorkbookProject e um projeto de instalação chamado ExcelWorkbookSetup. O projeto ExcelWorkbookSetup é configurado usando as mesmas etapas descritas acima, exceto para definir as chaves do registro.

Para adicionar o projeto de ação personalizada à sua solução do Visual Studio

1. Adicione um novo projeto de console .NET à solução clicando com o botão direito do mouse no **projeto de implantação de documentos do Office** na **Gerenciador de soluções**
2. Expanda **Adicionar** e clique em **novo projeto**.
3. Selecione o modelo de aplicativo de console e nomeie o projeto **AddCustomizationCustomAction**.

    ![Captura de tela do Gerenciador de Soluções-AddCustomizationCustomAction](media/setup-project-figure-15.jpg)
  
    **Figura 12: Gerenciador de Soluções-AddCustomizationCustomAction**

4. Adicione uma referência a esses assemblies:
    1. System.ComponentModel
    2. System.Configuration.Install
    3. Microsoft. VisualStudio. Tools. Applications
    4. Microsoft.VisualStudio.Tools.Applications.ServerDocument

5. Copie esse código em Program.cs ou Program. vb

```csharp
    using System;
    using System.IO;
    using System.Collections;
    using System.ComponentModel;
    using System.Configuration.Install;
    using Microsoft.VisualStudio.Tools.Applications;
    using Microsoft.VisualStudio.Tools.Applications.Runtime;

    namespace AddCustomizationCustomAction
    {
        [RunInstaller(true)]
        public class AddCustomizations : Installer
        {
            public AddCustomizations() : base() { }

            public override void Install(IDictionary savedState)
            {
                base.Install(savedState);

                //Get the CustomActionData Parameters
                string documentLocation = Context.Parameters.ContainsKey("documentLocation") ? Context.Parameters["documentLocation"] : String.Empty;
                string assemblyLocation = Context.Parameters.ContainsKey("assemblyLocation") ? Context.Parameters["assemblyLocation"] : String.Empty;
                string deploymentManifestLocation = Context.Parameters.ContainsKey("deploymentManifestLocation") ? Context.Parameters["deploymentManifestLocation"] : String.Empty;
                Guid solutionID = Context.Parameters.ContainsKey("solutionID") ? new Guid(Context.Parameters["solutionID"]) : new Guid();

                string newDocLocation = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), Path.GetFileName(documentLocation));

                try
                {
                    //Move the file and set the Customizations
                    if (Uri.TryCreate(deploymentManifestLocation, UriKind.Absolute, out Uri docManifestLocationUri))
                    {
                        File.Move(documentLocation, newDocLocation);
                        ServerDocument.RemoveCustomization(newDocLocation);
                        ServerDocument.AddCustomization(newDocLocation, assemblyLocation,
                                                        solutionID, docManifestLocationUri,
                                                        true, out string[] nonpublicCachedDataMembers);
                    }
                    else
                    {
                        LogMessage("The document could not be customized.");
                    }
                }
                catch (ArgumentException)
                {
                    LogMessage("The document could not be customized.");
                }
                catch (DocumentNotCustomizedException)
                {
                    LogMessage("The document could not be customized.");
                }
                catch (InvalidOperationException)
                {
                    LogMessage("The customization could not be removed.");
                }
                catch (IOException)
                {
                    LogMessage("The document does not exist or is read-only.");
                }
            }

            public override void Rollback(IDictionary savedState)
            {
                base.Rollback(savedState);
                DeleteDocument();
            }
            public override void Uninstall(IDictionary savedState)
            {
                base.Uninstall(savedState);
                DeleteDocument();
            }
            private void DeleteDocument()
            {
                string documentLocation = Context.Parameters.ContainsKey("documentLocation") ? Context.Parameters["documentLocation"] : String.Empty;

                try
                {
                    File.Delete(Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), Path.GetFileName(documentLocation)));
                }
                catch (Exception)
                {
                    LogMessage("The document doesn't exist or is read-only.");
                }
            }
            private void LogMessage(string Message)
            {
                if (Context.Parameters.ContainsKey("LogFile"))
                {
                    Context.LogMessage(Message);
                }
            }

            static void Main() { }
            }
    }
```

Para adicionar a personalização ao documento, você precisa ter a ID da solução de sua solução de nível de documento do VSTO. Esse valor é recuperado do arquivo de projeto do Visual Studio.

Para recuperar a ID da solução

1. No menu **Compilar** , clique em **Compilar solução** para criar a solução em nível de documento e adicione a propriedade ID da solução ao arquivo de projeto.
2. Na **Gerenciador de soluções**, clique com o botão direito do mouse no projeto de nível de documento **ExcelWorkbookProject**
3. Clique em **UnloadProject** para acessar o arquivo de projeto de dentro do Visual Studio.

    ![Captura de tela de Gerenciador de Soluções descarregamento da solução de documentos do Excel](media/setup-project-figure-16.jpg)

    **Figura 13: descarregamento da solução de documento do Excel**

4. Na **Gerenciador de soluções**, clique com o botão direito do mouse em **ExcelWorkbookProject** e clique em **EditExcelWorkbookProject. vbproj** ou **edite ExcelWorkbookProject. csproj**.
5. No editor de **ExcelWorkbookProject** , localize o elemento **SolutionID** dentro do elemento **PropertyGroup** .
6. Copie o valor de GUID deste elemento.

    ![Recuperando o SolutionId](media/setup-project-figure-17.jpg)

    **Figura 14: Recuperando o SolutionId**

7. Na **Gerenciador de soluções**, clique com o botão direito do mouse em **ExcelWorkbookProject** e clique em **recarregar projeto**.
8. Clique em **Sim** na caixa de diálogo que aparece para fechar o editor de **ExcelWorkbookProject** .
9. A **ID da solução** será usada na ação personalizada de instalação.

A última etapa é configurar a ação personalizada para as etapas de **instalação** e **desinstalação** .

### <a name="to-configure-the-setup-project"></a>Para configurar o projeto de instalação

1. Na **Gerenciador de soluções**, clique com o botão direito do mouse em **ExcelWorkbookSetup**, expanda **Adicionar** e clique em **saída do projeto**.
2. Na caixa de diálogo **Adicionar grupo de saída do projeto** , na lista **projeto** , clique em **AddCustomizationCustomAction**.
3. Selecione **saída primária** e clique em **OK** para fechar a caixa de diálogo e adicionar o assembly que contém a ação personalizada para o projeto de instalação.

    ![Captura de tela da ação personalizada do manifesto do documento – adicionar janela do grupo de saída do projeto](media/setup-project-figure-18.jpg)

    **Figura 15: ação personalizada do manifesto do documento – Adicionar grupo de saída do projeto**

4. Na **Gerenciador de soluções**, clique com o botão direito do mouse em **ExcelWorkbookSetup**.
5. Expanda **exibição** e clique em **ações personalizadas**.
6. No editor de **ações personalizadas (ExcelWorkbookSetup)** , clique com o botão direito do mouse em **ações personalizadas** e clique em **Adicionar ação personalizada**.
7. Na caixa de diálogo **selecionar item no projeto** , na lista **examinar** , clique em **pasta do aplicativo**. Selecione a **saída primária de AddCustomizationCustomAction (ativa)** e clique em **OK** para adicionar a ação personalizada à etapa de instalação.
8. No **nó instalar**, clique com o botão direito do mouse em **saída primária de AddCustomizationCustomAction (ativo)** e clique em **renomear**. Nomeie a ação personalizada **copiar documento para meus documentos e anexe a personalização**.
9. No **nó desinstalar**, clique com o botão direito do mouse em **saída primária de AddCustomizationCustomAction (ativo)** e clique em **renomear**. Nomeie a ação personalizada **remover documento da pasta documentos**.

    ![Captura de tela da janela ações personalizadas do manifesto do documento](media/setup-project-figure-19.jpg)

    **Figura 16: ações personalizadas do manifesto do documento**

10. No editor de **ações personalizadas (ExcelWorkbookSetup)** , clique com o botão direito do mouse em **copiar documento para meus documentos e anexe a personalização** e clique em **janela de propriedades**.
11. Na janela  **Propriedades** de CustomActionData, insira o local da DLL de personalização, o manifesto de implantação e o local do Microsoft Office documento. O SolutionId também é necessário.
12. Se você quiser registrar em log os erros de instalação em um arquivo, inclua um parâmetro de LogFile.
s
    ``` text
    /assemblyLocation="[INSTALLDIR]ExcelWorkbookProject.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbookProject.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx" /solutionID="Your Solution ID" /LogFile="[TARGETDIR]Setup.log"
    ```

    ![Captura de tela da ação personalizada para copiar o documento para meus documentos janela Propriedades](media/setup-project-figure-20.jpg)

    **Figura 17: ação personalizada para copiar o documento para meus documentos**

13. A ação personalizada para desinstalação precisa do nome do documento, você pode fornecer isso usando o mesmo parâmetro documentLocation no **CustomActionData**

    ``` text
    /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx"
    ```

14. Compile e implante o projeto **ExcelWorkbookSetup** .
15. Examine a pasta **meus documentos** e abra o arquivo ExcelWorkbookProject.xlsx.

## <a name="additional-resources"></a>Recursos adicionais

[Como instalar o Ferramentas do Visual Studio para o tempo de execução do Office](how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)

[Assemblies de interoperabilidade primários do Office](office-primary-interop-assemblies.md)

[Entradas de registro para suplementos do VSTO](registry-entries-for-vsto-add-ins.md)

[Visão geral de propriedades de documento personalizadas](custom-document-properties-overview.md)

[Especificando regiões de formulário no registro do Windows](/office/vba/outlook/concepts/creating-form-regions/specifying-form-regions-in-the-windows-registry)

[Concedendo confiança a documentos](granting-trust-to-documents.md)

## <a name="about-the-authors"></a>Sobre os autores

O Wouter van Vugt é um MVP da Microsoft com as tecnologias Office Open XML e um consultor independente que se concentra na criação de OBAs (Office Business Applicationss) com o SharePoint, Microsoft Office e tecnologias .NET relacionadas.
Wouter é um colaborador frequente em sites de comunidade de desenvolvedores, como o [msdn](/previous-versions/office/developer/office-2007/bb879915(v=office.12)). Ele publicou vários White papers e artigos, bem como um livro disponível na linha intitulada Open XML: explicou o livro eletrônico.
Wouter é o fundador da assessoria de código, uma empresa holandesa que se concentra em fornecer conteúdo técnico de ponta por meio de uma variedade de canais. Você pode saber mais sobre o Wouter lendo seu blog.

Ted Pattison é MVP do SharePoint, autor, instrutor e fundador de Ted Pattison Group. No Outono de 2005, Ted foi contratado pelo grupo de divulgação de plataforma de desenvolvedor da Microsoft para criar o currículo de treinamento de desenvolvedores de Ascend para o Windows SharePoint Services 3,0 e Microsoft Office SharePoint Server 2007. Desde esse momento, Ted tem se concentrado totalmente na conscientização de desenvolvedores profissionais em tecnologias do SharePoint 2007. Ted terminou de escrever um livro para a Microsoft Press intitulado Inside Windows SharePoint Services 3,0, que se concentra em como usar o SharePoint como uma plataforma de desenvolvimento para a criação de soluções de negócios. Ted também escreve uma coluna voltada para o desenvolvedor para a MSDN Magazine intitulada Office Space.
