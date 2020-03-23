---
title: Implantando um Visual Studio Tools para solução de escritório usando o Instalador do Windows
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 876781cb6967f5d10dddccd54a46e218170445ab
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79432360"
---
# <a name="deploying-a-visual-studio-tools-for-office-solution-using-windows-installer"></a>Implantando um Visual Studio Tools para solução de escritório usando o Instalador do Windows

## <a name="summary"></a>Resumo

Saiba como implantar uma solução de complemento ou nível de documento do Microsoft Visual Studio Tools for Office (VSTO) usando um projeto do Visual Studio Installer.

Wouter van Vugt, Advogado de Código

Ted Pattison, Grupo Ted Pattison

Este artigo foi atualizado pela Microsoft com permissão dos autores originais.

**Aplica-se a:** Visual Studio Tools para Office, Microsoft Office, Microsoft Visual Studio.

## <a name="overview"></a>Visão geral

Você pode desenvolver uma solução VSTO e implantar a solução usando um pacote do Windows Installer. Essa discussão inclui etapas para a implantação de um simples Complemento de Escritório.

## <a name="deployment-methods"></a>Métodos de implantação

ClickOnce pode ser usado facilmente para criar configurações para seus Add-ins e soluções. No entanto, ele não pode instalar Add-ins que requerem privilégios administrativos, como complementos de nível de máquina.

Os complementos que requerem privilégios administrativos podem ser instalados usando o Windows Installer, mas isso requer mais esforço para criar a configuração.

Para obter uma visão geral de como implantar uma solução VSTO usando o ClickOnce, consulte [Implantar uma solução do Office usando ClickOnce](deploying-an-office-solution-by-using-clickonce.md).

## <a name="deploying-office-solutions-that-target-the-vsto-runtime"></a>Implantando soluções do Office que visam o tempo de execução do VSTO

Os pacotes ClickOnce e Windows Installer precisam fazer as mesmas tarefas rudimentares ao instalar uma solução office.

1. Instale componentes pré-requisitos no computador do usuário.
2. Implante os componentes específicos para a solução.
3. Para add-ins, crie entradas de registro.
4. Confie na solução para permitir que ela seja executada.

### <a name="required-prerequisite-components-on-the-target-computer"></a>Componentes pré-requisitos necessários no computador de destino

Aqui está a lista de software que deve ser instalado no computador para executar soluções VSTO:

- Microsoft Office 2010 ou mais novo.
- O Microsoft .NET Framework 4 ou mais novo.
- Microsoft Visual Studio 2010 Tools for Office Runtime.
  O tempo de execução fornece um ambiente que gerencia add-ins e soluções em nível de documento. Uma versão do Runtime é distribuída com o Microsoft Office, mas você pode querer redistribuir uma versão específica com o seu complemento.
- Os conjuntos interop primários para o Microsoft Office, se você não estiver usando tipos de interop incorporados.
- Quaisquer montagens de utilidades referenciadas por projetos.

### <a name="specific-components-for-the-solution"></a>Componentes específicos para a solução

O pacote do instalador deve instalar esses componentes no computador do usuário:

- O documento do Microsoft Office, se você criar uma solução de nível de documento.
- A montagem de personalização e quaisquer assembléias que ele requer.
- Componentes adicionais, como arquivos de configuração.
- O manifesto de aplicação (.manifesto).
- O manifesto de implantação (.vsto).

### <a name="registry-entries-for-add-ins"></a>Inscrições de registro para Add-ins

O Microsoft Office usa entradas de registro para localizar e carregar add-ins. Essas entradas de registro devem ser criadas como parte do processo de implantação. Para obter mais informações sobre essas entradas de registro, consulte [entradas de Registro para Add-ins VSTO](registry-entries-for-vsto-add-ins.md).

Os complementos do Outlook que exibem regiões de formulários personalizados exigem entradas adicionais de registro que permitem que as regiões do formulário sejam identificadas. Para obter mais informações sobre entradas de registro, consulte [Inscrições para regiões do formulário do Outlook](registry-entries-for-vsto-add-ins.md#OutlookEntries).

As soluções de nível de documento não exigem entradas de registro. Em vez disso, as propriedades dentro do documento são usadas para localizar a personalização. Para obter mais informações sobre essas propriedades, consulte [Visão geral de propriedades de documentos personalizados](custom-document-properties-overview.md).

### <a name="trusting-the-vsto-solution"></a>Confiando na solução VSTO

Para que uma personalização seja executada, uma solução deve ser confiável pela máquina. O Add-in pode ser confiável assinando o manifesto com um certificado, criando um relacionamento de confiança com uma lista de inclusão ou instalando-o em um local confiável na máquina.

Para obter mais informações sobre como obter um certificado para assinatura, consulte [ClickOnce Deployment e Authenticode](../deployment/clickonce-and-authenticode.md). Para obter mais informações sobre soluções confiáveis, consulte [Trusting Office Solutions usando listas de inclusão](trusting-office-solutions-by-using-inclusion-lists.md). Você pode adicionar uma entrada de lista de inclusão com uma ação personalizada no arquivo do Instalador do Windows. Para obter mais informações sobre como ativar a lista de inclusão, consulte [Como: Configurar a segurança da lista de inclusão](how-to-configure-inclusion-list-security.md).

Se nenhuma opção for usada, um prompt de confiança é exibido ao usuário para permitir que ele decida se confia na solução.

Para obter mais informações sobre segurança relacionadas a soluções de nível de documento, consulte [Conceder confiança em documentos](granting-trust-to-documents.md).

## <a name="creating-a-basic-installer"></a>Criando um instalador básico

Os modelos de projeto de configuração e implantação estão incluídos na extensão [Microsoft Visual Studio Installer Projects](https://marketplace.visualstudio.com/items?itemName=visualstudioclient.MicrosoftVisualStudio2017InstallerProjects) que está disponível para download.

Para criar um instalador para uma solução office, essas tarefas devem ser cumpridas:

- Adicione os componentes da solução de escritório que serão implantadas.
- Para add-ins em nível de aplicativo, configure as chaves de registro.
- Configure os componentes pré-requisitos para que possam ser instalados nos computadores dos usuários finais.
- Configure as condições de lançamento para verificar se os componentes pré-requisitos necessários estão disponíveis. As condições de lançamento podem ser usadas para bloquear a instalação se todos os pré-requisitos necessários não estiverem instalados.

O primeiro passo é criar o projeto de configuração.

### <a name="to-create-the-addin-setup-project"></a>Para criar o projeto AddIn Setup

1. Abra o Projeto Office AddIn que deseja implantar. Para este exemplo, estamos usando um Add-in do Excel chamado ExcelAddIn.
2. Com o Projeto Office Aberto, no menu **Arquivo,** **expanda adicionar** e clique em **Novo Projeto** para adicionar um novo projeto.
::: moniker range="=vs-2017"
3. Na caixa de diálogo **Adicionar novo projeto,** expanda outros tipos de **projeto** no painel tipos **de projeto,** depois **expanda a configuração e a implantação** e selecione o Visual Studio **Installer**.
4. No painel **Templates,** selecione Projeto de **configuração** do grupo de modelos instalados do **Visual Studio.**
::: moniker-end
::: moniker range="=vs-2019"
3. Na **caixa de diálogo Adicionar um novo projeto,** selecione o modelo **'Projeto de configuração'.**
4. Clique em **Avançar**.
::: moniker-end

5. Na **caixa Nome,** **digite OfficeAddInSetup**.
::: moniker range="=vs-2017"
6. Clique **em Abrir** para criar o novo projeto de configuração.
::: moniker-end
::: moniker range="=vs-2019"
6. Clique **em Criar** para criar o novo projeto de configuração.
::: moniker-end

O Visual Studio abre o File System Explorer para o novo projeto de configuração. O File System Explorer permite adicionar arquivos ao projeto de configuração.

   ![Captura de tela do File System Explorer para o projeto de configuração](media/setup-project-figure-1.png)

   **Figura 1: Explorador do sistema de arquivos para o projeto de configuração**

O projeto de configuração precisa implantar o ExcelAddIn. Você pode configurar o projeto de configuração para esta tarefa adicionando a saída do projeto ExcelAddIn ao projeto de configuração.

### <a name="to-add-the-exceladdin-project-output"></a>Para adicionar a saída do projeto ExcelAddIn

1. No **Solution Explorer**, clique com o botão direito do mouse **OfficeAddInSetup,** clique **em Adicionar** e, em seguida, saída do **projeto**.
2. Na **caixa de** diálogo Adicionar grupo de saída de projeto, selecione o **ExcelAddIn** na lista de projetos e **a saída principal**.
3. Clique em **OK** para adicionar a saída do projeto ao projeto de configuração.

    ![Captura de tela da caixa de diálogo grupo de saída do projeto de configuração adicionar projeto](media/setup-project-figure-2.png)

    **Figura 2: Conjunto Projeto Adicionar diálogo grupo de saída do projeto**

O projeto de configuração precisa implantar o manifesto de implantação e o manifesto de aplicação. Adicione esses dois arquivos ao projeto de configuração como arquivos autônomos da pasta de saída do projeto ExcelAddIn.

### <a name="to-add-the-deployment-and-application-manifests"></a>Para adicionar a implantação e os manifestos de aplicativos

1. No **Solution Explorer**, clique com o botão direito do mouse **OfficeAddInSetup,** clique **em Adicionar**e clique **em Arquivo**.
2. Na caixa de diálogo **Adicionar arquivos,** navegue até o diretório de saída **ExcelAddIn.** Normalmente, o diretório de saída é a subpasta de versão do **bin\\** do diretório raiz do projeto, dependendo da configuração de compilação selecionada.
3. Selecione os arquivos **ExcelAddIn.vsto** e **ExcelAddIn.dll.manifest** e clique **em Abrir** para adicionar esses dois arquivos ao projeto de configuração.

    ![Captura de tela do aplicativo e se manifesta na solução explorer](media/setup-project-figure-3.jpg)

    **Figura 3: Manifestos de aplicação e implantação para o Add-in in Solution Explorer**

Fazendo referência ao ExcelAddIn inclui todos os componentes que o ExcelAddIn requer. Esses componentes devem ser excluídos e implantados usando pacotes pré-requisitos para permitir que sejam registrados corretamente. Além disso, os Termos de Licença de Software devem ser exibidos e aceitos antes do início da instalação.

### <a name="to-exclude-the-exceladdin-project-dependencies"></a>Para excluir as dependências do projeto ExcelAddIn

1. No **solution explorer**, no nó **OfficeAddInSetup,** selecione todos os itens de dependência abaixo do item **Dependências Detectadas,** exceto no **Microsoft .NET Framework** ou em qualquer conjunto que termine com ** \*. Utilities.dll**. Os conjuntos de utilitários devem ser implantados juntamente com sua aplicação.
2. Clique com o botão direito do mouse no grupo e selecione **Propriedades**.
3. Na janela **Propriedades,** **altere** a propriedade Excluir para **True** para excluir as assembléias dependentes do projeto de configuração. Certifique-se de não excluir quaisquer conjuntos de Utilitários.

    ![Captura de tela do Solution Explorer mostrando as dependências para excluir](media/setup-project-figure-4.jpg)

    **Figura 4: Excluindo dependências**

Você pode configurar seu pacote do Windows Installer para instalar componentes pré-requisitos adicionando um programa de configuração, também conhecido como bootstrapper. Este programa de configuração pode instalar os componentes pré-requisitos, um processo chamado bootstrapping.

Para o **ExcelAddIn,** esses pré-requisitos devem ser instalados antes que o Add-in possa ser executado corretamente:

- A versão Microsoft .NET Framework que a Solução do Escritório tem como alvo.
- Microsoft Visual Studio 2010 Tools para Office Runtime.

Configurar componentes dependentes como pré-requisitos

1. No **Solution Explorer,** clique com o botão direito do mouse no projeto **OfficeAddInSetup** e selecione **Propriedades**.
2. A caixa de diálogo **'Páginas de propriedade OfficeAddInSetup'** é exibida.
3. Clique no botão **Pré-requisitos.**
4. Na caixa de diálogo Pré-requisitos, selecione a versão correta do .NET Framework e do Microsoft Visual Studio Tools for Office Runtime.

    ![Captura de tela da caixa de diálogo pré-requisitos](media/setup-project-figure-5.png)

    **Figura 5: Caixa de diálogo pré-requisitos**

    > [!NOTE]
    >Alguns dos pacotes pré-requisitos configurados em seu Projeto de Configuração do Visual Studio dependem da configuração de compilação selecionada. Você deve selecionar os componentes pré-requisitos certos para cada configuração de compilação que você usa.

O Microsoft Office localiza add-ins usando chaves de registro. As teclas da\_\_colmeia hkey current user são usadas para registrar o complemento para cada usuário individual. As teclas sob\_\_a colmeia HKEY LOCAL MACHINE são usadas para registrar o complemento para todos os usuários da máquina. Para obter mais informações sobre as chaves do registro, consulte [entradas de registro para add-ins VSTO](registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-the-registry"></a>Para configurar o registro

1. No **Solution Explorer**, clique com o botão direito **do mouse OfficeAddInSetup**.
2. Expandir **a exibição**.
3. Clique **em Registry** para abrir a janela do editor de registro.
4. No editor **Registry (OfficeAddInSetup),** expanda **o HKEY\_LOCAL\_MACHINE** e, em seguida, o **Software**.
5. Exclua a ** \[tecla\]Manufacturer**?encontrada no software **HKEY\_LOCAL\_MACHINE\\**.
6. Expanda **o Usuário\_\_ATUAL do HKEY** e, em seguida, o **Software**.
7. Exclua ** \[\] ** a chave do fabricante encontrada no **software de usuário\_\_\\atual HKEY**.
8. Para adicionar as chaves de registro para a instalação de entrada com o botão direito do mouse na tecla **User/Machine Hive, selecione** **Nova chave**. Use o **software** de texto para o nome da nova chave. Clique com o botão direito do mouse na tecla **Software** recém-criada e crie uma nova chave com o texto **Microsoft**.
9. Use um processo semelhante para criar toda a hierarquia de chaves necessária para o registro de complemento:

    **Software\\de hive\\\\de\\\\usuário/máquina\\Microsoft Office Excel Addins SampleCompany.ExcelAddIn**

    O Nome da Empresa é frequentemente usado como um prefixo para o nome do complemento para fornecer exclusividade.

10. Clique com o botão direito do mouse na **tecla SampleCompany.ExcelAddIn,** selecione **Novo**e clique **em Valor de Seqüência**. Use o texto **Descrição** do nome.
11. Use esta etapa para adicionar mais três valores:
    - **AmigávelNome** do tipo **String**
    - **CargaComportamento** do tipo **DWORD**
    - **Manifesto** do tipo **String**

12. Clique com o botão direito do mouse no valor **descrição** no editor de registro e clique em **Janela propriedades**. Na **janela Propriedades,** digite **Excel Demo AddIn** para a propriedade Valor.
13. Selecione a tecla **FriendlyName** no editor de registro. Na **janela Propriedades,** altere a propriedade **Valor** para **Excel Demo AddIn**.
14. Selecione a tecla **LoadBehavior** no editor do registro. Na **janela Propriedades,** altere a propriedade **Valor** para **3.** O valor 3 para o LoadBehavior indica que o complemento deve ser carregado na inicialização do aplicativo host. Para obter mais informações sobre o comportamento de carga, consulte [entradas de Registro para Add-ins VSTO](registry-entries-for-vsto-add-ins.md).

15. Selecione a tecla **Manifest** no editor do registro. Na **janela Propriedades,** altere a propriedade **Valor** para **file:///[TARGETDIR]ExcelAddIn.vsto|vstolocal**

    ![Captura de tela do Editor de Registro](media/setup-project-figure-6.png)

    **Figura 6: Configuração de chaves de registro**

      O tempo de execução do VSTO usa essa chave de registro para localizar o manifesto de implantação. A macro [TARGETDIR] será substituída pela pasta para a qual o complemento está instalado. A macro incluirá o caractere trailing \, de modo que o nome de arquivo do manifesto de implantação deve ser ExcelAddIn.vsto sem o caractere \.
      O **postfix vstolocal** informa ao tempo de execução do VSTO que o Add-in deve ser carregado a partir deste local em vez do cache ClickOnce. A remoção deste postfix fará com que o tempo de execução copie a personalização no cache ClickOnce.

   >[!WARNING]
   >Você deve ter muito cuidado com o Editor de Registro no Visual Studio. Por exemplo, se você acidentalmente definir DeleteAtUninstall para a chave errada, você pode excluir uma parte ativa do registro, deixando o computador do usuário em um estado inconsistente, ou pior ainda pior.

Versões de 64 bits do Office usarão a colmeia de registro de 64 bits para procurar complementos. Para registrar add-ins a colmeia de registro de 64 bits, a plataforma-alvo do projeto de configuração deve ser definida apenas como 64 bits.

1. Selecione o projeto **OfficeAddInSetup** no explorador de soluções.
2. Vá para a janela **Propriedades** e defina a propriedade **TargetPlatform** como **x64**.

A instalação de um Complemento para versões de 32 bits e 64 bits do Office exigirá que você crie dois pacotes MSI separados. Um para 32 bits e outro para 64 bits.

  ![Captura de tela da janela propriedades mostrando a plataforma de destino para registrar add-ins com office de 64 bits](media/setup-project-figure-7.jpg)

  **Figura 7: Plataforma-alvo para registrar Add-ins com Office de 64 bits**

Se o pacote MSI for usado para instalar o Add-in ou a solução, ele poderá ser instalado sem que os pré-requisitos necessários sejam instalados. Você pode usar condições de lançamento no MSI para bloquear a instalação do Complemento se os pré-requisitos não estiverem instalados.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime"></a>Configure uma condição de lançamento para detectar o tempo de execução do VSTO

1. No **Solution Explorer**, clique com o botão direito **do mouse OfficeAddInSetup**.
2. Expandir **a exibição**.
3. Clique **em Condições de lançamento**.
4. No editor **'Condições de lançamento',** clique com o botão direito **do mouse's Requirements on Target Machine**e clique em Adicionar condição de lançamento de registro **.** Essa condição de pesquisa pode procurar no registro uma chave que o tempo de execução VSTO instala. O valor da chave está então disponível para as várias peças do instalador através de uma propriedade nomeada. A condição de lançamento usa a propriedade definida pela condição de pesquisa para verificar se há um determinado valor.
5. No editor **'Condições de lançamento',** selecione a condição **de pesquisa Pesquisar para RegistryEntry1,** clicar com o botão direito do mouse na condição e selecionar Janela **propriedades**.

6. Na janela **Propriedades,** defina essas propriedades:
   1. Defina o valor de **(Nome)** **para pesquisar o tempo de execução vsto 2010**.
   2. Alterar o valor da **propriedade** para **VSTORUNTIMEREDIST**.
   3. Defina o valor do **RegKey** para **software\\Microsoft\\VSTO Runtime Setup\\v4R**
   4. Deixe a propriedade **Root** definida como **vsdrrHKLM**.
   5. Alterar a propriedade **Valor** para **Versão**.

7. No editor **'Condições de lançamento',** selecione a condição de lançamento **Condition1,** clique com o botão direito do mouse na condição e selecione **'Janela de propriedades].**
8. Na janela Propriedades, defina essas propriedades:
   1. Defina o **(Nome)** para verificar a **disponibilidade de tempo de execução do VSTO 2010**.
   2. Alterar o valor da **Condição** para **\>VSTORUNTIMEREDIST ="10.0.30319"**
   3. Deixe a propriedade **InstallURL** em branco.
   4. Defina a **mensagem** para **as ferramentas do Visual Studio 2010 para o Office Runtime não está instalada. Por favor, execute Setup.exe para instalar o Add-in**.

        ![Captura de tela da janela propriedades para verificar a condição de lançamento de disponibilidade de tempo de execução](media/setup-project-figure-8.jpg)

        **Figura 8: Janela de propriedades para verificar a condição de lançamento de disponibilidade de tempo de execução**

 A condição de lançamento acima verifica explicitamente a presença do tempo de execução DO VSTO quando ele é instalado pelo pacote bootstrapper.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime-installed-by-office"></a>Configure uma condição de lançamento para detectar o tempo de execução VSTO instalado pelo Office

1. No editor **'Condições de lançamento',** clique com o botão direito do mouse **Na máquina alvo de pesquisa**e clique em Adicionar pesquisa de **registro**.
2. Selecione a condição **de pesquisa Pesquisar para RegistryEntry1,** clicar com o botão direito do mouse na condição e selecionar Janela **propriedades**.
3. Na janela **Propriedades,** defina essas propriedades:
    1. Defina o valor de **(Nome)** **para procurar o Office VSTO Runtime**.
    2. Alterar o valor da **propriedade** para **OfficeRuntime**.
    3. Defina o valor do **RegKey** para **software\\Microsoft\\VSTO Runtime Setup\\v4**.
    4. Deixe a propriedade **Root** definida como **vsdrrHKLM**.
    5. Alterar a propriedade **Valor** para **Versão**.

4. No editor **'Condições de lançamento',** selecione a condição de lançamento de disponibilidade de **tempo de execução do VsTO 2010** definida anteriormente, clique com o botão direito do mouse na condição e selecione **Janela propriedades**.

5. Alterar o valor da propriedade **Condição** para **VSTORUNTIMEREDIST \>="10.0.30319" OU OFFICERUNTIME\>="10.0.21022"**. Os números da versão talvez sejam diferentes para você, dependendo das versões do tempo de execução que o seu Add-in requer.

    ![Captura de tela do Windows propriedades para a condição de lançamento](media/setup-project-figure-9.jpg)
  
    **Figura 9: Propriedades windows para verificar a disponibilidade de tempo de execução através da condição de lançamento redist ou office**

Se um Complemento tiver como alvo o .NET Framework 4, ou mais novo, os Tipos dentro das Assembléias De Interop Primárias (PIA), referenciadas, podem ser incorporados no conjunto VSTO.

Para verificar se os Tipos de Interop serão incorporados no seu Complemento, realizando as seguintes etapas:

1. Expanda o nó de referências no Solution Explorer
2. Selecione uma das referências PIA, por exemplo, **Office**.
3. Exibir as janelas de propriedades clicando em F4 ou selecionando Propriedades no menu de contexto Deassembléias.
4. Verifique o valor da propriedade **Incorporar tipos de interop**.

Se o valor estiver definido **como True,** então os Tipos estão sendo incorporados e você pode pular para baixo para [**a seção Para construir a**](#to-build-the-setup-project) seção projeto de configuração.

Para obter mais informações, consulte [Equivalência de tipo e tipos de interop incorporados](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types)

### <a name="to-configure-launch-conditions-to-detect-that-for-office-pias"></a>Para configurar as condições de lançamento para detectar isso para PIAs do Office

1. No editor **'Condições de lançamento',** clique com o botão direito **do mouse's Requirements on Target Machine**e clique em Adicionar condição de lançamento do **instalador do Windows .** Esta condição de lançamento procura um Office PIA procurando o ID de componente específico.
2. Clique com o botão direito do mouse **Em Procurar componente1** e clique **em 'Janelas de propriedades'** para mostrar as propriedades da condição de lançamento.
3. Na **janela Propriedades,** defina essas propriedades:

    1. Alterar o valor da propriedade **(Nome)** **para Procurar escritório compartilhado PIA**
    2. Alterar o valor do **ComponentID** para O ID do componente para o componente Office que você está usando. Você pode encontrar a lista de Ids de componentes na tabela abaixo, por exemplo **{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}**.
    3. Alterar o valor da **propriedade para** **HASSHAREDPIA**.

4. No editor **Condições de lançamento (OfficeAddInSetup),** clique com o botão direito do mouse **Em Condição1** e clique **em Janela propriedades** para mostrar as propriedades da condição de lançamento.

5. Alterar estas propriedades da **Condição1**:

    1. Alterar o **(Nome)** para Verificar a **disponibilidade pia compartilhada do escritório**.
    2. Alterar a **Condição** para **HASSHAREDPIA**.
    3. Deixe **a InstallUrl** em branco.
    4. Não está disponível a **mensagem** para **um componente necessário para interagir com o Excel. Por favor, execute setup.exe**.

    ![Captura de tela da janela propriedades para a condição de lançamento pia compartilhada do escritório de verificação](media/setup-project-figure-10.jpg)
  
    **Figura 10: Janela de propriedades para a condição de lançamento pia compartilhada do escritório de verificação**

### <a name="component-ids-of-the-primary-interop-assemblies-for-microsoft-office"></a>IDs de componentes das assembléias de interop primárias para o Microsoft Office

|Montagem interop primária|Office 2010|Office 2013|Escritório 2013 (64 bits)|Office 2016|Escritório 2016 (64 bits)|
|------------------------|------------------------|------------------------|------------------------|------------------------|------------------------|
|Excel|{EA7564AC-C67D-4868-BE5C-26E4FC2223FF}|{C8A65ABE-3270-4FD7-B854-50C8082C8F39}|{E3BD1151-B9CA-4D45-A77E-51A6E0ED322A}|C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|{C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|
|InfoPath|{4153F732-D670-4E44-8AB7-500F2B576BDA}|{0F825A16-25B2-4771-A497-FC8AF3B355D8}|{C5BBD36E-B320-47EF-A512-556B99CB7E41}|-|-|
|Outlook|{1D844339-3DAE-413E-BC13-62D6A52816B2}|{F9F828D5-9F0B-46F9-9E3E-9C59F3C5E136}|{7824A03F-28CC-4371-BC54-93D15EFC1E7F}|{7C6D92EF-7B45-46E5-8670-819663220E4E}|{7C6D92EF-7B45-46E5-8670-819663220E4E}|
|PowerPoint|{EECBA6B8-3A62-44AD-99EB-8666265466F9}|{813139Ad-6DAB-4DDD-8C6D-0CA30D073B41}|{05758318-BCFD-4288-AD8D-81185841C235}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|
|Visio|{3EA123B5-6316-452E-9d51-A489E06E2347}|{C1713368-12A8-41F1-ACA1-934B01AD6EEB}|{2CC0B221-22D2-4C15-A9FB-DE818E51AF75}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|
|Word|{8B74A499-37F8-4DEA-B5A0-D72FC501CEFA}|{9FE736B7-B1EE-410C-8D07-082891C3DAC8}|{13C07AF5-B206-4A48-BB5B-B802233E3CA}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|
|Formulários Microsoft 2.0|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{A5A30117-2D2A-4C5C-B3C8-8897AC32C2AC}|-|-|
|Microsoft Graph|{011B9112-EBB1-4A6C-86CB-C2FDC9EA7B0E}|{52DA4B37-B8EB-4B7F-89C1-824654CE4C70}|{24706F33-F0CE-4EB4-BC91-9E935394F510}|-|-|
|Tag inteligente|{7102C98C-EF47-4F04-A227-FE33650BF954}|{487A7921-EB3A-4262-BB5B-A5736B732486}|{74EFC1F9-747D-4867-B951-EFCF29F51AF7}|-|-|
|Escritório Compartilhado|{64E2917e-AA13-4CA4-BFFE-EA6EDA3AFCB4}|{6A174BDB-0049-4D1C-86EF-3114CB0C4C4E}|{76601EBB-44A7-49EE-8DE3-7b7b9D7EBB05}|{625F5772-C1B3-497E-8ABE-7254EDB00506}|{625F5772-C1B3-497E-8ABE-7254EDB00506}|
|Project|{957A4EC0-E67B-4E86-A383-6AF7270B216A}|{1C50E422-24FA-44A9-A120-E88280C8C341}|{706D7F44-8231-489D-9B25-3025ADE9F114}|{107BCD9A-F1DC-4004-A444-33706FC10058}|{107BCD9A-F1DC-4004-A444-33706FC10058}|

  ![Captura de tela das condições finais de lançamento](media/setup-project-figure-11.jpg)

  **Figura 11: Condições finais de lançamento**

Você pode refinar ainda mais as condições de lançamento para a instalação do ExcelAddIn. Por exemplo, talvez seja útil verificar se o aplicativo de destino real do Office está instalado.

### <a name="to-build-the-setup-project"></a>Para construir o projeto de configuração

1. No **Solution Explorer,** clique com o botão direito do mouse no projeto **OfficeAddInSetup** e clique **em Build**.
2. Usando **o Windows Explorer,** navegue até o diretório de saída do projeto **OfficeAddInSetup** e vá para a pasta Liberar ou Depurar, dependendo da configuração de compilação selecionada. Copie todos os arquivos da pasta para um local que os usuários possam acessar.

Para testar a configuração do ExcelAddIn

1. Navegue até o local onde você copiou **OfficeAddInSetup** para.
2. Clique duas vezes no arquivo setup.exe para instalar o **complemento OfficeAddInSetup.** Aceite quaisquer Termos de licença de software que apareçam e complete o assistente de configuração para instalar o complemento no computador do usuário.

A solução do Excel Office deve ser instalada e executada a partir do local especificado durante a configuração.

## <a name="additional-requirements-for-document-level-solutions"></a>Requisitos adicionais para soluções em nível de documento

A implantação de soluções de nível de documento requer algumas etapas de configuração diferentes no projeto de configuração do Windows Installer.

Aqui está uma lista de etapas básicas necessárias para implantar uma solução de nível de documento:

- Crie o Projeto de Configuração do Estúdio Visual.
- Adicione a saída primária da solução de nível de documento. A saída principal também inclui o documento do Microsoft Office.
- Adicione a implantação e os manifestos do aplicativo como arquivos soltos.
- Exclua os componentes dependentes do pacote do instalador (exceto para quaisquer conjuntos de utilitários).
- Configure pacotes pré-requisitos.
- Configure as condições de lançamento.
- Construa o projeto de configuração e copie os resultados para o local de implantação.
- Implante a solução de nível de documento no computador do usuário executando a configuração.
- Atualize as propriedades do documento personalizado, se necessário.

### <a name="changing-the-location-of-the-deployed-document"></a>Alterando a localização do documento implantado

As propriedades dentro de um documento do Office são usadas para localizar soluções de nível de documento. Se o documento estiver instalado na mesma pasta do conjunto VSTO, não serão necessárias alterações. No entanto, se ele for instalado em diferentes pastas, essas propriedades precisarão ser atualizadas durante a configuração.

Para obter mais informações sobre essas propriedades do documento, consulte Visão geral de propriedades de [documentos personalizados](custom-document-properties-overview.md).

Para alterar essas propriedades, você precisa usar uma ação personalizada durante a configuração.

O exemplo a seguir usa uma solução de nível de documento chamada ExcelWorkbookProject e um projeto de configuração chamado ExcelWorkbookSetup. O projeto ExcelWorkbookSetup é configurado usando as mesmas etapas descritas acima, exceto para definir as chaves do registro.

Para adicionar o projeto de ação personalizado à sua solução Visual Studio

1. Adicione um novo projeto de console .NET à solução clicando com o botão direito do projeto de **implantação de documentos** do Office no Explorador de **soluções**
2. ExpandA **adicionar** e clique **em Novo Projeto**.
3. Selecione o modelo do aplicativo de console e nomeie o projeto **AddCustomizationCustomAction**.

    ![Captura de tela do Solution Explorer - AddCustomizationCustomAction](media/setup-project-figure-15.jpg)
  
    **Figura 12: Explorador de soluções - AdicionarCustomizaçãoCustomAction**

4. Adicionar uma referência a esses conjuntos:
    1. System.ComponentModel
    2. System.Configuration.Install
    3. Microsoft.VisualStudio.Tools.Aplicativos
    4. Microsoft.VisualStudio.Tools.Applications.ServerDocument

5. Copie este código em Program.cs ou Program.vb

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

Para adicionar a personalização ao documento, você precisa ter o ID de solução da sua solução de nível de documento VSTO. Esse valor é recuperado do arquivo de projeto Visual Studio.

Para recuperar o ID da solução

1. No menu **Build,** clique **em Criar solução** para criar a solução de nível de documento e adicionar a propriedade de ID da solução ao arquivo do projeto.
2. No **Solution Explorer**, clique com o botão direito do mouse no projeto de nível de documento **ExcelWorkbookProject**
3. Clique **em DescarregarProjeto** para acessar o arquivo do projeto de dentro do Visual Studio.

    ![Captura de tela da solução explorer descarregando solução de documento excel](media/setup-project-figure-16.jpg)

    **Figura 13: Descarregar solução de documento excel**

4. No **Solution Explorer**, clique com o botão direito do **mouse ExcelWorkbookProject** e clique **em EditExcelWorkbookProject.vbproj** ou **Edit ExcelWorkbookProject.csproj**.
5. No editor do **ExcelWorkbookProject,** localize o elemento **SolutionID** dentro do elemento **PropertyGroup.**
6. Copie o valor GUID deste elemento.

    ![Recuperando a soluçãoID](media/setup-project-figure-17.jpg)

    **Figura 14: Recuperando a soluçãoID**

7. No **Solution Explorer,** clique com o botão direito do mouse **excelWorkbookProject** e clique em **Recarregar projeto**.
8. Clique em **Sim** na caixa de diálogo que aparece para fechar o editor **do ExcelWorkbookProject.**
9. O **ID da solução** será usado na Ação Personalizada de Instalação.

O último passo é configurar a ação personalizada para as etapas **Instalar** e **Desinstalar.**

### <a name="to-configure-the-setup-project"></a>Para configurar o projeto de configuração

1. No **Solution Explorer**, clique com o botão direito do **mouse ExcelWorkbookSetup,** **expanda Adicionar** e clique em Saída de **projeto**.
2. Na caixa de diálogo Adicionar grupo **de saída de** projeto, na lista **Projeto,** clique em **AdicionarCustomizationCustomAction**.
3. Selecione **Saída primária** e clique em **OK** para fechar a caixa de diálogo e adicionar o conjunto que contém a ação personalizada ao projeto de configuração.

    ![Captura de tela da ação personalizada manifesto de documento - adicionar janela grupo de saída de projeto](media/setup-project-figure-18.jpg)

    **Figura 15: Ação personalizada do manifesto do documento - adicionar grupo de saída do projeto**

4. No **Solution Explorer**, clique com o botão direito do **mouse ExcelWorkbookSetup**.
5. Expandir **a exibição** e clicar **em Ações Personalizadas**.
6. No editor **Ações Personalizadas (ExcelWorkbookSetup),** clique com o botão **direito do mouse em Ações Personalizadas** e clique **em Adicionar ação personalizada**.
7. Na caixa de diálogo **Selecionar item no projeto,** na lista **Procurar em** inato, clique em Pasta **de aplicativo**. Selecione **Saída primária de AddCustomizationCustomAction(ativo)** e clique em **OK** para adicionar a ação personalizada à etapa Instalar.
8. No **nó Instalar,** clique com o botão direito do mouse **na saída principal de AdicionarPersonalizaçãoCustomAction (Ativa)** e clique em **Renomear**. Nomeie o documento de ação personalizada **Copie o documento para meus documentos e anexe a personalização**.
9. No **nó 'Desinstalar',** clique com o botão direito do mouse **na saída principal de AdicionarCustomizaçãoCustomAction(Ativa)** e clique em **Renomear**. Nomeie a ação personalizada **Remova o documento da pasta Documentos**.

    ![Captura de tela da janela Ações Personalizadas do Manifesto de Documento](media/setup-project-figure-19.jpg)

    **Figura 16: Ações aduaneiras de manifesto de documentos**

10. No editor **Ações Personalizadas (ExcelWorkbookSetup),** clique com o botão direito do mouse **Copiar documento em Meus Documentos e anexar personalização** e clicar em **Janela propriedades**.
11. Na **janela** **Propriedades CustomActionData,** digite a localização da DLL de personalização, o manifesto de implantação e a localização do documento do Microsoft Office. O SolutionID também é necessário.
12. Se desejar registrar quaisquer erros de configuração em um arquivo, inclua um parâmetro LogFile.
s
    ``` text
    /assemblyLocation="[INSTALLDIR]ExcelWorkbookProject.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbookProject.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx" /solutionID="Your Solution ID" /LogFile="[TARGETDIR]Setup.log"
    ```

    ![Captura de tela da ação personalizada para copiar documento para a janela Propriedades de meus documentos](media/setup-project-figure-20.jpg)

    **Figura 17: Ação personalizada para copiar documento em meus documentos**

13. A Ação Personalizada para Desinstalar precisa do nome do documento, você pode fornecer isso usando o mesmo parâmetro de localização do documento no **CustomActionData**

    ``` text
    /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx"
    ```

14. Compilar e implantar o projeto **ExcelWorkbookSetup.**
15. Procure na pasta **Meus documentos** e abra o arquivo ExcelWorkbookProject.xlsx.

## <a name="additional-resources"></a>Recursos adicionais

[Como: Instalar o Visual Studio Tools para o Office Runtime](how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)

[Assemblies de interoperabilidade primários do Office](office-primary-interop-assemblies.md)

[Inscrições de registro para add-ins VSTO](registry-entries-for-vsto-add-ins.md)

[Visão geral de propriedades de documento personalizadas](custom-document-properties-overview.md)

[Especificando regiões de formulário no Registro do Windows](/office/vba/outlook/concepts/creating-form-regions/specifying-form-regions-in-the-windows-registry)

[Concedendo confiança a documentos](granting-trust-to-documents.md)

## <a name="about-the-authors"></a>Sobre os autores

Wouter van Vugt é um MVP da Microsoft com tecnologias Office Open XML e um consultor independente com foco na criação de OBAs (Office Business Applications, aplicativos de negócios do Office) com sharepoint, Microsoft Office e tecnologias .NET relacionadas.
Wouter é um contribuinte frequente para sites de desenvolvedores da comunidade, como [OpenXmlDeveloper.org](http://openxmldeveloper.org/) e [MSDN.](/previous-versions/office/developer/office-2007/bb879915(v=office.12)) Ele publicou vários white papers e artigos, bem como um livro disponível na linha intitulado Open XML: Explained e-book.
Wouter é o fundador da Code-Counsel, uma empresa holandesa focada em fornecer conteúdo técnico de ponta através de uma variedade de canais. Você pode saber mais sobre Wouter lendo seu blog e visitando o [site do Code-Counsel](http://www.code-counsel.net/).

Ted Pattison é MVP do SharePoint, autor, treinador e fundador do Ted Pattison Group. No outono de 2005, Ted foi contratado pelo grupo De Sanearismo da Plataforma de Desenvolvedores da Microsoft para criar o currículo de treinamento de desenvolvedores Ascend para o Windows SharePoint Services 3.0 e o Microsoft Office SharePoint Server 2007. Desde então, Ted tem sido inteiramente focado em educar desenvolvedores profissionais sobre as tecnologias SharePoint 2007. Ted terminou de escrever um livro para a Microsoft Press intitulado Inside Windows SharePoint Services 3.0 que se concentra em como usar o SharePoint como uma plataforma de desenvolvimento para a construção de soluções de negócios. Ted também escreve uma coluna focada em desenvolvedores para a Revista MSDN intitulada Office Space.
