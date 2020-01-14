---
title: Instalando um aplicativo de shell isolado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], deploying shell-based applications
- Visual Studio shell, deploying shell-based applications
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: 41
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0adc81cfe9ea4462940c31a02c6429be89709565
ms.sourcegitcommit: 9a66f1c31cc9eba0b5231af72da1d18761a9c56a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75944257"
---
# <a name="installing-an-isolated-shell-application"></a>Instalar um aplicativo de Shell isolado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para instalar um aplicativo de Shell, você deve executar as etapas a seguir.  
  
- Prepare sua solução.  
  
- Crie um pacote de Windows Installer (MSI) para seu aplicativo.  
  
- Crie um bootstrapper de instalação.  
  
  Todo o código de exemplo deste documento é proveniente do [exemplo de implantação do Shell](https://code.msdn.microsoft.com/Sample-setup-program-for-81ca73f7), que pode ser baixado na Galeria de códigos do site do MSDN. O exemplo mostra os resultados da execução de cada uma dessas etapas.  
  
## <a name="prerequisites"></a>{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}  
 Para executar os procedimentos descritos neste tópico, as ferramentas a seguir devem ser instaladas em seu computador.  
  
- O SDK do Visual Studio  
  
- O [conjunto de ferramentas XML Windows Installer](https://documentation.help/WiX-Toolset/index.html/) versão 3,6  
  
  O exemplo também requer o SDK de modelagem e visualização da Microsoft, que nem todos os shells exigem.  
  
## <a name="preparing-your-solution"></a>Preparando sua solução  
 Por padrão, os modelos de shell são criados para pacotes VSIX, mas esse comportamento destina-se principalmente a fins de depuração. Ao implantar um aplicativo de Shell, você deve usar pacotes do MSI para permitir o acesso ao registro e para reinicializações durante a instalação. Para preparar seu aplicativo para a implantação do MSI, execute as etapas a seguir.  
  
#### <a name="to-prepare-a-shell-application-for-msi-deployment"></a>Para preparar um aplicativo de Shell para a implantação do MSI  
  
1. Edite cada arquivo. vsixmanifest em sua solução.  
  
     No elemento `Identifier`, adicione um elemento `InstalledByMSI` e um elemento `SystemComponent` e, em seguida, defina seus valores como `true`.  
  
     Esses elementos impedem que o instalador do VSIX tente instalar seus componentes e o usuário a desinstale usando a caixa de diálogo **extensões e atualizações** .  
  
2. Para cada projeto que contém um manifesto do VSIX, edite as tarefas de compilação para gerar o conteúdo para o local do qual o MSI será instalado. Inclua o manifesto do VSIX na saída da compilação, mas não crie um arquivo. vsix.  
  
## <a name="creating-an-msi-for-your-shell"></a>Criando um MSI para o Shell  
 Para criar seu pacote MSI, recomendamos que você use o [conjunto de ferramentas Windows Installer XML](https://documentation.help/WiX-Toolset/index.html) porque ele oferece maior flexibilidade do que um projeto de instalação padrão.  
  
 No arquivo Product. wxs, defina os blocos de detecção e o layout dos componentes do Shell.  
  
 Em seguida, crie entradas do registro, tanto no arquivo. reg para sua solução quanto em ApplicationRegistry. wxs.  
  
### <a name="detection-blocks"></a>Blocos de detecção  
 Um bloco de detecção consiste em um elemento `Property` que especifica um pré-requisito para detectar e um elemento `Condition` que especifica uma mensagem a ser retornada se o pré-requisito não estiver presente no computador. Por exemplo, seu aplicativo de shell exigirá o Microsoft Visual Studio Shell redistribuível, e o bloco de detecção será semelhante à marcação a seguir.  
  
```xml  
<Property Id="ISOSHELLSFX">  
  <RegistrySearch Id="IsoShellSfx" Root="HKLM" Key="Software\Microsoft\DevDiv\vs\Servicing\\$(var.ShellVersion)\IsoShell\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
<Property Id="INTSHELLSFX">  
  <RegistrySearch Id="IntShellSfx" Root="HKLM" Key="SOFTWARE\Microsoft\DevDiv\vs\Servicing\$(var.ShellVersion)\devenv\$(var.ProductLanguage)" Name="Install" Type="raw" />  
</Property>  
  
<Condition Message="This application requires $(var.IsoShellName).  Please install $(var.IsoShellName) then run this installer again.">  
  <![CDATA[Installed OR ISOSHELLSFX]]>  
</Condition>  
<Condition Message="This application requires $(var.IntShellName).  Please install $(var.IntShellName) then run this installer again.">  
  <![CDATA[Installed OR INTSHELLSFX]]>  
</Condition>  
  
```  
  
### <a name="layout-of-shell-components"></a>Layout dos componentes do Shell  
 Você deve adicionar elementos para identificar a estrutura do diretório de destino e os componentes a serem instalados.  
  
##### <a name="to-set-the-layout-of-shell-components"></a>Para definir o layout dos componentes do Shell  
  
1. Crie uma hierarquia de elementos de `Directory` para representar todos os diretórios a serem criados no sistema de arquivos no computador de destino, como mostra o exemplo a seguir.  
  
    ```xml  
    <Directory Id="TARGETDIR" Name="SourceDir">  
      <Directory Id="ProgramFilesFolder">  
        <Directory Id="CompanyDirectory" Name="$(var.CompanyName)">  
          <Directory Id="INSTALLDIR" Name="$(var.FullProductName)">  
            <Directory Id="ExtensionsFolder" Name="Extensions" />  
            <Directory Id="Folder1033" Name="1033" />  
          </Directory>  
        </Directory>  
      </Directory>  
      <Directory Id="ProgramMenuFolder">  
        <Directory Id="ApplicationProgramsFolder" Name="$(var.FullProductName)"/>  
      </Directory>  
    </Directory>  
    ```  
  
     Esses diretórios são referidos por `Id` quando são especificados arquivos que devem ser instalados.  
  
2. Identifique os componentes que o Shell e o aplicativo de shell exigem, como mostra o exemplo a seguir.  
  
    > [!NOTE]
    > Alguns elementos podem se referir a definições em outros arquivos. wxs.  
  
    ```xml  
    <Feature Id="ProductFeature" Title="$(var.ShortProductName)Shell" Level="1">  
      <ComponentGroupRef Id="ApplicationGroup" />  
      <ComponentGroupRef Id="HelpAboutPackage" />  
      <ComponentRef Id="GeneralProfile" />  
      <ComponentGroupRef Id="EditorAdornment"/>        
      <ComponentGroupRef Id="SlideShowDesignerGroup"/>  
  
      <!-- Note: The following ComponentGroupRef is required to pull in generated authoring from project references. -->  
      <ComponentGroupRef Id="Product.Generated" />  
    </Feature>  
    ```  
  
    1. O elemento `ComponentRef` refere-se a outro arquivo. wxs que identifica os arquivos que o componente atual exige. Por exemplo, GeneralProfile tem a seguinte definição em HelpAbout. wxs.  
  
        ```xml  
        <Fragment Id="FragmentProfiles">  
          <DirectoryRef Id="INSTALLDIR">  
            <Directory Id="ProfilesFolder" Name="Profiles">  
              <Component Id='GeneralProfile' Guid='*'>  
                <File Id='GeneralProfile' Name='General.vssettings' DiskId='1' Source='$(var.BuildOutputDir)Profiles\General.vssettings' KeyPath='yes' />  
              </Component>  
            </Directory>  
          </DirectoryRef>  
        </Fragment>  
        ```  
  
         O elemento `DirectoryRef` especifica onde esses arquivos vão para o computador do usuário. O elemento `Directory` especifica que ele será instalado em um subdiretório, e cada elemento `File` representa um arquivo que é compilado ou que existe como parte da solução e identifica onde esse arquivo pode ser encontrado quando o arquivo MSI é criado.  
  
    2. O elemento `ComponentGroupRef` refere-se a um grupo de outros componentes (ou componentes e grupos de componentes). Por exemplo, `ComponentGroupRef` sob o filewxs é definido da seguinte maneira em Application.  
  
        ```xml  
        <ComponentGroup Id="ApplicationGroup">  
          <ComponentGroupRef Id="DebuggerProxy" />  
          <ComponentRef Id="MasterPkgDef" />  
          <ComponentRef Id="SplashResource" />  
          <ComponentRef Id="IconResource" />  
          <ComponentRef Id="WinPrfResource" />  
          <ComponentRef Id="AppExe" />  
          <ComponentRef Id="AppConfig" />  
          <ComponentRef Id="AppPkgDef" />  
          <ComponentRef Id="AppPkgDefUndef" />  
          <ComponentRef Id="$(var.ShortProductName)UI1033" />  
          <ComponentRef Id="ApplicationShortcut"/>  
          <ComponentRef Id="ApplicationRegistry"/>  
        </ComponentGroup>  
        ```  
  
    > [!NOTE]
    > As dependências necessárias para aplicativos de Shell (isolados) são: DebuggerProxy, MasterPkgDef, Resources (especialmente o arquivo. winprf), Application e PkgDefs.  
  
### <a name="registry-entries"></a>Entradas do Registro  
 O modelo de projeto Shell (isolado) inclui um arquivo *ProjectName*. reg para chaves do registro a serem mescladas na instalação. Essas entradas de registro devem fazer parte do MSI para fins de instalação e limpeza. Você também deve criar blocos de registro correspondentes em ApplicationRegistry. wxs.  
  
##### <a name="to-integrate-registry-entries-into-the-msi"></a>Para integrar entradas de registro no MSI  
  
1. Na pasta de **personalização do Shell** , abra *ProjectName*. reg.  
  
2. Substitua todas as instâncias do token $RootFolder $ pelo caminho do diretório de instalação de destino.  
  
3. Adicione outras entradas de registro que seu aplicativo requer.  
  
4. Abra ApplicationRegistry. wxs.  
  
5. Para cada entrada de registro no *ProjectName*. reg, adicione um bloco de registro correspondente, como mostra os exemplos a seguir.  
  
    |*ProjectName*.reg|ApplicationRegisty.wxs|  
    |-----------------------|----------------------------|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}]<br /><br /> @ = "Objeto DTE PhotoStudio"|\<RegistryKey ID = ' DteClsidRegKey ' root = ' HKCR ' Key = ' $ (var. DteClsidRegKey) ' action = ' createAndRemoveOnUninstall ' ><br /><br /> \<REGISTRYVALUE tipo = ' String ' name = ' @ ' value = ' $ (var. ShortProductName) objeto DTE '/><br /><br /> \</RegistryKey>|  
    |[HKEY_CLASSES_ROOT\CLSID\\{bb431796-a179-4df7-b65d-c0df6bda7cc6}\LocalServer32]<br /><br /> @="$RootFolder$\PhotoStudio.exe"|\<RegistryKey ID = ' DteLocSrv32RegKey ' root = ' HKCR ' Key = ' $ (var. DteClsidRegKey) \LocalServer32 ' action = ' createAndRemoveOnUninstall ' ><br /><br /> \<REGISTRYVALUE tipo = ' String ' name = ' @ ' value = ' [INSTALLDIR] $ (var. ShortProductName). exe '/><br /><br /> \</RegistryKey>|  
  
     Neste exemplo, var. DteClsidRegKey resolve para a chave do registro na linha superior. Var. ShortProductName resolve para `PhotoStudio`.  
  
## <a name="creating-a-setup-bootstrapper"></a>Criando um bootstrapper de instalação  
 O MSI concluído será instalado somente se todos os pré-requisitos forem instalados primeiro. Para facilitar a experiência do usuário final, crie um programa de instalação que colete e instale todos os pré-requisitos antes de instalar seu aplicativo. Para garantir uma instalação bem-sucedida, execute estas ações:  
  
- Impor a instalação pelo administrador.  
  
- Detectar se o Shell do Visual Studio (isolado) está instalado.  
  
- Execute um ou ambos os instaladores do Shell na ordem.  
  
- Tratar solicitações de reinício.  
  
- Execute o MSI.  
  
### <a name="enforcing-installation-by-administrator"></a>Impondo a instalação pelo administrador  
 Esse procedimento é necessário para permitir que o programa de instalação acesse os diretórios necessários, como \Program Files\\.  
  
##### <a name="to-enforce-installation-by-administrator"></a>Para impor a instalação pelo administrador  
  
1. Abra o menu de atalho para o projeto de instalação e, em seguida, escolha **Propriedades**.  
  
2. Em **Propriedades de configuração/vinculador/arquivo de manifesto**, defina **nível de execução do UAC** como **requireAdministrator**.  
  
     Essa propriedade coloca o atributo que exige que o programa seja executado como administrador no arquivo de manifesto inserido.  
  
### <a name="detecting-shell-installations"></a>Detectando instalações do Shell  
 Para determinar se o Shell do Visual Studio (isolado) deve ser instalado, primeiro determine se ele já está instalado verificando o valor do registro de HKLM\Software\Microsoft\DevDiv\vs\Servicing\ShellVersion\isoshell\LCID\Install.  
  
> [!NOTE]
> Esses valores também são lidos pelo bloco de detecção de Shell em Product. wxs.  
  
 HKLM\Software\Microsoft\AppEnv\14.0\ShellFolder especifica o local em que o Shell do Visual Studio foi instalado e você pode verificar se há arquivos ali.  
  
 Para obter um exemplo de como detectar uma instalação do Shell, consulte a função `GetProductDirFromReg` de Utilities. cpp no exemplo de implantação do Shell.  
  
 Se um ou ambos os shells do Visual Studio que seu pacote requer não estiverem instalados no computador, você deverá adicioná-los à lista de componentes a serem instalados. Para obter um exemplo, consulte a função `ComponentsPage::OnInitDialog` de ComponentsPage. cpp no exemplo de implantação do Shell.  
  
### <a name="running-the-shell-installers"></a>Executando os instaladores do Shell  
 Para executar os instaladores do Shell, chame os redistribuíveis do shell do Visual Studio usando os argumentos de linha de comando corretos. No mínimo, você deve usar os argumentos de linha de comando **/norestart/q** e observar o código de retorno para determinar o que deve ser feito em seguida. O exemplo a seguir executa o Shell (isolado) redistribuível.  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### <a name="running-the-shell-language-pack-installers"></a>Executando os instaladores do pacote de idiomas do Shell  
 Se, em vez disso, você descobrir que o Shell ou os shells foram instalados e precisar apenas de um pacote de idiomas, você poderá instalar os pacotes de idiomas como mostra o exemplo a seguir.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### <a name="deciphering-return-values"></a>Decifrando valores de retorno  
 Em alguns sistemas operacionais, a instalação do shell do Visual Studio (isolado) exigirá uma reinicialização. Essa condição pode ser determinada pelo código de retorno da chamada para `ExecCmd`.  
  
|Valor de retorno|Descrição|  
|------------------|-----------------|  
|ERROR_SUCCESS|Instalação concluída. Agora você pode instalar seu aplicativo.|  
|ERROR_SUCCESS_REBOOT_REQUIRED|Instalação concluída. Você pode instalar o aplicativo após a reinicialização do computador.|  
|3015|A instalação está em andamento. É necessária uma reinicialização do computador para continuar a instalação.|  
  
### <a name="handling-restarts"></a>Manipulando reinicializações  
 Quando você executou o instalador do shell usando o argumento **/norestart** , especificou que ele não reiniciaria o computador nem pediria que o computador fosse reiniciado. No entanto, uma reinicialização pode ser necessária e você deve garantir que o instalador continue depois que o computador for reiniciado.  
  
 Para tratar as reinicializações corretamente, verifique se apenas um programa de instalação está definido como retomar e se o processo de retomada será manipulado corretamente.  
  
 Se ERROR_SUCCESS_REBOOT_REQUIRED ou 3015 for retornado, seu código deverá reiniciar o computador antes que a instalação continue.  
  
 Para lidar com as reinicializações, execute estas ações:  
  
- Defina o registro para retomar a instalação quando o Windows for iniciado.  
  
- Execute uma reinicialização dupla do bootstrapper.  
  
- Exclua a chave ResumeData do instalador do Shell.  
  
- Reinicie o Windows.  
  
- Redefina o caminho inicial do MSI.  
  
### <a name="setting-the-registry-to-resume-setup-when-windows-starts"></a>Definindo o registro para retomar a instalação quando o Windows é iniciado  
 A chave do registro HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce\ é executada na inicialização do sistema com permissões administrativas e, em seguida, é apagada. O HKEY_CURRENT_USER contém uma chave semelhante, mas é executado como um usuário normal e não é apropriado para instalações. Você pode retomar a instalação colocando um valor de cadeia de caracteres na chave RunOnce que chama o instalador. No entanto, recomendamos que você chame o instalador usando um parâmetro **/Restart** ou semelhante para notificar o aplicativo que ele está retomando em vez de iniciar. Você também pode incluir parâmetros para indicar onde você está no processo de instalação, o que é especialmente útil em instalações que podem exigir várias reinicializações.  
  
 O exemplo a seguir mostra um valor de chave do registro RunOnce para retomar uma instalação.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### <a name="installing-double-restart-of-bootstrapper"></a>Instalando o reinício duplo do bootstrapper  
 Se a instalação for usada diretamente do RunOnce, a área de trabalho não poderá ser carregada completamente. Para disponibilizar a interface do usuário completa, você deve criar outra execução de instalação e encerrar a instância do RunOnce.  
  
 Você deve executar novamente o programa de instalação para que ele obtenha as permissões corretas, e você deve fornecer informações suficientes para saber onde você parou antes da reinicialização, como mostra o exemplo a seguir.  
  
```  
if (_cmdLineInfo.IsRestart())  
{  
    TCHAR path[MAX_PATH]={0};  
    GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR));      
    ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL );  
}  
  
```  
  
### <a name="deleting-the-shell-installer-resumedata-key"></a>Excluindo a chave ResumeData do instalador do Shell  
 O instalador do Shell define a chave do registro HKLM\Software\Microsoft\VisualStudio\14.0\Setup\ResumeData com dados para retomar a instalação após a reinicialização. Como seu aplicativo, não o instalador do Shell, está retomando, exclua essa chave do registro, como mostra o exemplo a seguir.  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData"));  
RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### <a name="restarting-windows"></a>Reiniciando o Windows  
 Depois de definir as chaves de Registro necessárias, você pode reiniciar o Windows. O exemplo a seguir invoca os comandos de reinicialização para diferentes sistemas operacionais Windows.  
  
```  
OSVERSIONINFO ov;  
HANDLE htoken ;  
//Ask for the SE_SHUTDOWN_NAME token as this is needed by the thread calling for a system shutdown.  
if (OpenProcessToken(GetCurrentProcess(), TOKEN_ADJUST_PRIVILEGES | TOKEN_QUERY, &htoken))  
{  
    LUID luid ;  
    LookupPrivilegeValue(NULL, SE_SHUTDOWN_NAME, &luid) ;  
    TOKEN_PRIVILEGES    privs ;  
    privs.Privileges[0].Luid = luid ;  
    privs.PrivilegeCount = 1 ;  
    privs.Privileges[0].Attributes = SE_PRIVILEGE_ENABLED ;  
    AdjustTokenPrivileges(htoken, FALSE, &privs, 0, (PTOKEN_PRIVILEGES) NULL, 0) ;  
}   
  
//Use InitiateSystemShutdownEx to avoid unexpected restart message box  
try  
{              
    if ( (ov.dwMajorVersion > 5) || ( (ov.dwMajorVersion == 5) && (ov.dwMinorVersion  > 0) ))  
    {  
        bExitWindows = InitiateSystemShutdownEx(0, _T(""), 0, TRUE, TRUE, REASON_PLANNED_FLAG);  
    }  
    else  
    {  
#pragma prefast(suppress:380,"ignore warning about legacy api")  
        bExitWindows = InitiateSystemShutdown(0, _T(""), 0, TRUE, TRUE);  
    }  
}  
catch(...)  
{  
    //advapi32.dll call not available! Will not restart!  
}  
  
```  
  
### <a name="resetting-the-start-path-of-msi"></a>Redefinindo o caminho inicial do MSI  
 Antes da reinicialização, o diretório atual é o local do seu programa de instalação, mas, após a reinicialização, o local se torna o diretório system32. O programa de instalação deve redefinir o diretório atual antes de cada chamada de MSI, como mostra o exemplo a seguir.  
  
```  
CString GetSetupPath()  
{  
    TCHAR file[MAX_PATH];  
    GetModuleFileName(NULL, file, MAX_PATH * sizeof(TCHAR));  
    CString path(file);  
    int fpos = path.ReverseFind('\\');  
    if (fpos != -1)  
    {  
        path = path.Left(fpos + 1);  
    }  
  
    return path;  
}  
  
```  
  
### <a name="running-the-application-msi"></a>Executando o MSI do aplicativo  
 Depois que o instalador do shell do Visual Studio retornar ERROR_SUCCESS, você poderá executar o MSI para seu aplicativo. Como o programa de instalação está fornecendo a interface do usuário, inicie o MSI no modo silencioso ( **/q**) e com Logging ( **/l**), como mostra o exemplo a seguir.  
  
```cpp#  
TCHAR temp[MAX_PATH];  
GetTempPath(MAX_PATH, temp);  
  
CString boutiqueInstallCmd, msi, log;  
CString cmdLine(MAKEINTRESOURCE("msiexec /q /I %s /L*vx %s REBOOT=ReallySuppress"));  
CString name(MAKEINTRESOURCE("PhotoStudioIntShell.msi"));  
log.Format(_T("\"%s%s.log\""), temp, name);  
msi.Format(_T("\"%s%s\""), GetSetupPath(), name);  
boutiqueInstallCmd.Format(cmdLine, msi, log);  
  
//TODO: You can use MSI API to gather and present install progress feedback from your MSI.  
dwResult = ExecCmd(boutiqueInstallCmd, FALSE);  
```  
  
## <a name="see-also"></a>Veja também  
 [Passo a passo: criar um aplicativo básico de Shell isolado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)
