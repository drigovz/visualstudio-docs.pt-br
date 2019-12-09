---
title: Entradas de registro para suplementos do VSTO
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- LoadBehavior entry
- add-ins [Office development in Visual Studio], registry entries
- registry keys [Office development in Visual Studio]
- application-level add-ins [Office development in Visual Studio], registry entries
- registry entries [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a98164488d548a15c07e67b9a02cad2341f7300b
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985646"
---
# <a name="registry-entries-for-vsto-add-ins"></a>Entradas de registro para suplementos do VSTO
  Você deve criar um conjunto específico de entradas de registro ao implantar suplementos do VSTO que são criados usando o Visual Studio. Essas entradas de registro fornecem informações que permitem que o aplicativo Microsoft Office descubra e carregue o suplemento do VSTO.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Quando você cria seu projeto, o Visual Studio cria essas entradas de registro no computador de desenvolvimento para que você possa executar e depurar facilmente o suplemento do VSTO. Se você usar o ClickOnce para implantar seu suplemento do VSTO, as entradas do registro serão criadas automaticamente no computador do usuário final. Se você usar Windows Installer para implantar o suplemento do VSTO, deverá configurar o projeto do InstallShield Limited Edition para criar as entradas do registro no computador do usuário final.

 Para obter mais informações sobre como as entradas do registro são usadas durante o processo de carregamento para suplementos do VSTO, consulte [arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md).

> [!NOTE]
> Neste tópico, a ID do *suplemento* de texto representa uma ID exclusiva para seu suplemento do VSTO. Por padrão, a ID é o nome do seu assembly de suplemento do VSTO.

## <a name="register-vsto-add-ins-for-the-current-user-vs-all-users"></a>Registrar suplementos do VSTO para o usuário atual versus todos os usuários
 Quando um suplemento do VSTO é instalado, ele pode ser registrado de duas maneiras:

- Somente para o usuário atual (ou seja, ele está disponível somente para o usuário que está conectado ao computador quando o suplemento do VSTO está instalado). Nesse caso, as entradas do registro são criadas no **HKEY_CURRENT_USER**.

- Para todos os usuários (ou seja, qualquer usuário que faça logon no computador pode usar o suplemento do VSTO). Nesse caso, as entradas do registro são criadas em **HKEY_LOCAL_MACHINE**.

  Todos os suplementos do VSTO que você cria usando o Visual Studio podem ser registrados para o usuário atual. No entanto, os suplementos do VSTO podem ser registrados para todos os usuários somente em determinados cenários. Esses cenários dependem da versão do Microsoft Office no computador e de como o suplemento do VSTO foi implantado.

### <a name="microsoft-office-version"></a>Versão do Microsoft Office
 Os aplicativos do Office podem carregar suplementos do VSTO que são registrados em **HKEY_LOCAL_MACHINE** ou **HKEY_CURRENT_USER**.

 Para carregar os suplementos do VSTO que estão registrados em **HKEY_LOCAL_MACHINE**, os computadores devem ter o pacote de atualização 976477 instalado. Para obter mais informações, consulte [http://go.microsoft.com/fwlink/?LinkId=184923](https://support.microsoft.com/help/976811/a-2007-office-system-application-does-not-load-an-add-in-that-is-devel).

### <a name="deployment-type"></a>Tipo de implantação
 Se você usar o ClickOnce para implantar um suplemento do VSTO, o suplemento do VSTO só poderá ser registrado para o usuário atual. Isso ocorre porque o ClickOnce só dá suporte à criação de chaves em **HKEY_CURRENT_USER**. Se você quiser registrar um suplemento do VSTO para todos os usuários em um computador, deverá usar Windows Installer para implantar o suplemento do VSTO. Para obter mais informações sobre esses tipos de implantação, consulte [implantar uma solução do Office usando o ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md) e [implantar uma solução do Office usando Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).

## <a name="registry-entries"></a>Entradas do Registro
 As entradas do registro do suplemento do VSTO necessárias estão localizadas na seguinte chave do registro para todos os aplicativos, exceto o Visio, em que a *raiz* é **HKEY_CURRENT_USER** ou **HKEY_LOCAL_MACHINE**.

 **Todos os aplicativos, exceto o Visio**

|Versão do Office|Caminho de configuração|
|--------------------|------------------------|
|32 bits|*Root*\Software\Microsoft\Office\\*nome do aplicativo*\Addins\\*ID do suplemento*|
|64 bits|*Root*\Software\Wow6432Node\Microsoft\Office\\*nome do aplicativo*\Addins\\*ID do suplemento*|

 **Visio**

|Versão do Office|Caminho de configuração|
|--------------------|------------------------|
|32 bits|*ID do suplemento*\\\Software\Microsoft\Visio\Addins *raiz*|
|64 bits|*ID do suplemento*\\\Software\Wow6432Node\Visio\Addins *raiz*|

 A tabela a seguir lista as entradas nessa chave do registro.

|Entrada|Digite|Valor|
|-----------|----------|-----------|
|**Descrição**|REG_SZ|Necessário. Uma breve descrição do suplemento do VSTO.<br /><br /> Essa descrição é exibida quando o usuário seleciona o suplemento do VSTO no painel de **suplementos** da caixa de diálogo **opções** no aplicativo Microsoft Office.|
|**FriendlyName**|REG_SZ|Necessário. Um nome descritivo do suplemento do VSTO que é exibido na caixa de diálogo **suplementos de com** no aplicativo Microsoft Office. O valor padrão é a ID do suplemento do VSTO.|
|**LoadBehavior**|REG_DWORD|Necessário. Um valor que especifica quando o aplicativo tenta carregar o suplemento do VSTO e o estado atual do suplemento do VSTO (carregado ou descarregado).<br /><br /> Por padrão, essa entrada é definida como 3, o que especifica que o suplemento do VSTO é carregado na inicialização. Para obter mais informações, veja [valores de LoadBehavior](#LoadBehavior). **Observação:**  Se um usuário desabilitar o suplemento do VSTO, essa ação modificará o valor **LoadBehavior** no hive do registro **HKEY_CURRENT_USER** . Para cada usuário, o valor do valor **LoadBehavior** no hive HKEY_CURRENT_USER substitui o **LoadBehavior** padrão definido no hive **HKEY_LOCAL_MACHINE** .|
|**Manifesto**|REG_SZ|Necessário. O caminho completo do manifesto de implantação para o suplemento do VSTO. O caminho pode ser um local no computador local, um compartilhamento de rede (UNC) ou um servidor Web (HTTP).<br /><br /> Se você usar Windows Installer para implantar a solução, deverá adicionar o prefixo **file:///** ao caminho do **manifesto** . Você também deve acrescentar a cadeia de caracteres  **&#124;vstolocal** (ou seja, o **&#124;** caractere de pipe seguido por **vstolocal**) ao final deste caminho. Isso garante que sua solução seja carregada a partir da pasta de instalação, em vez do cache do ClickOnce. Para obter mais informações, consulte [implantar uma solução do Office usando Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md). **Observação:**  Quando você cria um suplemento do VSTO no computador de desenvolvimento, o Visual Studio acrescenta automaticamente a cadeia  **&#124;** de caracteres vstolocal a essa entrada de registro.|

### <a name="OutlookEntries"></a>Entradas de registro para regiões de formulário do Outlook
 Se você criar uma região de formulário personalizada em um suplemento do VSTO para o Outlook, as entradas adicionais do registro serão usadas para registrar a região do formulário com o Outlook. Essas entradas são criadas sob uma chave de registro diferente para cada classe de mensagem à qual a região de formulário dá suporte. Essas chaves do registro estão no seguinte local, em que *root* é **HKEY_CURRENT_USER** ou **HKEY_LOCAL_MACHINE**.

 *Classe de mensagem* de\\\Software\Microsoft\Office\Outlook\FormRegions *raiz*

 Assim como as outras entradas de registro compartilhadas por todos os suplementos do VSTO, o Visual Studio cria as entradas do registro de região de formulário no computador de desenvolvimento quando você cria seu projeto. Se você usar o ClickOnce para implantar seu suplemento do VSTO, as entradas do registro serão criadas automaticamente no computador do usuário final. Se você usar Windows Installer para implantar o suplemento do VSTO, deverá configurar o projeto do InstallShield Limited Edition para criar as entradas do registro no computador do usuário final.

 Para obter mais informações sobre as entradas de registro de região de formulário, consulte [especificar o local de uma região de formulário em um formulário personalizado](/office/vba/outlook/Concepts/Creating-Form-Regions/specify-the-location-of-a-form-region-in-a-custom-form). Para obter mais informações sobre as regiões de formulário do Outlook, consulte [criar regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md).

## <a name="LoadBehavior"></a>Valores de LoadBehavior
 A entrada **LoadBehavior** sob a *raiz*\Software\Microsoft\Office\\*nome do aplicativo*\Addins\\chave de *ID de suplemento* contém uma combinação bit-a-ponto de valores que especificam o comportamento de tempo de execução do suplemento do VSTO. O menor bit de ordem (valores 0 e 1) indica se o suplemento do VSTO está atualmente descarregado ou carregado. Outros bits indicam quando o aplicativo tenta carregar o suplemento do VSTO.

 Normalmente, a entrada **LoadBehavior** deve ser definida como 0, 3 ou 16 (em decimal) quando o suplemento do VSTO é instalado nos computadores dos usuários finais. Por padrão, o Visual Studio define a entrada **LoadBehavior** de seu suplemento do VSTO como 3 quando você o compila ou publica.

 A tabela a seguir lista todos os valores possíveis da entrada **LoadBehavior** . Algumas descrições nesta tabela referem-se ao carregamento de um suplemento do VSTO manual ou programaticamente. Para carregar um suplemento do VSTO manualmente, marque a caixa de seleção ao lado do suplemento do VSTO na caixa de diálogo **suplementos do com** no aplicativo. Para carregar um suplemento do VSTO programaticamente, defina a propriedade <xref:Microsoft.Office.Core.COMAddIn.Connect%2A> do objeto <xref:Microsoft.Office.Core.COMAddIn> que representa o suplemento do VSTO como **true**.

|Valor (em decimal)|Status do suplemento do VSTO|Comportamento de carregamento do suplemento do VSTO|Descrição|
|--------------------------|-------------------------|--------------------------------|-----------------|
|0|Descarregado|Não carregar automaticamente|O aplicativo nunca tenta carregar o suplemento do VSTO automaticamente. O usuário pode tentar carregar manualmente o suplemento do VSTO ou o suplemento do VSTO pode ser carregado programaticamente.<br /><br /> Se o suplemento do VSTO for carregado com êxito, o valor **LoadBehavior** permanecerá 0, mas o status do suplemento do VSTO na caixa de diálogo **suplementos do com** será atualizado para indicar que o suplemento do VSTO está carregado.|
|1|Carregado|Não carregar automaticamente|O aplicativo nunca tenta carregar o suplemento do VSTO automaticamente. O usuário pode tentar carregar manualmente o suplemento do VSTO ou o suplemento do VSTO pode ser carregado programaticamente.<br /><br /> Embora a caixa de diálogo **suplementos de com** indique que o suplemento do VSTO é carregado depois que o aplicativo é iniciado, o suplemento do VSTO não é carregado até que seja carregado manualmente ou programaticamente.<br /><br /> Se o aplicativo carregar o suplemento do VSTO com êxito, o valor **LoadBehavior** será alterado para 0 e permanecerá em 0 depois que o aplicativo for fechado.|
|2|Descarregado|Carregar na inicialização|O aplicativo não tenta carregar o suplemento do VSTO automaticamente. O usuário pode tentar carregar manualmente o suplemento do VSTO ou o suplemento do VSTO pode ser carregado programaticamente.<br /><br /> Se o aplicativo carregar o suplemento do VSTO com êxito, o valor **LoadBehavior** mudará para 3 e permanecerá em 3 depois que o aplicativo for fechado.|
|3|Carregado|Carregar na inicialização|O aplicativo tenta carregar o suplemento do VSTO quando o aplicativo é iniciado. Esse é o valor padrão quando você cria ou publica um suplemento do VSTO no Visual Studio.<br /><br /> Se o aplicativo carregar o suplemento do VSTO com êxito, o valor **LoadBehavior** permanecerá 3. Se ocorrer um erro ao carregar o suplemento do VSTO, o valor **LoadBehavior** será alterado para 2 e permanecerá em 2 depois que o aplicativo for fechado.|
|8|Descarregado|Carregar sob demanda|O aplicativo não tenta carregar o suplemento do VSTO automaticamente. O usuário pode tentar carregar manualmente o suplemento do VSTO ou o suplemento do VSTO pode ser carregado programaticamente.<br /><br /> Se o aplicativo carregar o suplemento do VSTO com êxito, o valor **LoadBehavior** mudará para 9.|
|9|Carregado|Carregar sob demanda|O suplemento do VSTO será carregado somente quando o aplicativo exigir, como quando um usuário clicar em um elemento da interface do usuário que usa a funcionalidade no suplemento do VSTO (por exemplo, um botão personalizado na faixa de bits).<br /><br /> Se o aplicativo carregar o suplemento do VSTO com êxito, o valor **LoadBehavior** permanecerá em 9, mas o status do suplemento do VSTO na caixa de diálogo **suplementos do com** será atualizado para indicar que o suplemento do VSTO está carregado no momento. Se ocorrer um erro ao carregar o suplemento do VSTO, o valor **LoadBehavior** será alterado para 8.|
|16|Carregado|Carregar pela primeira vez e carregar sob demanda|Defina esse valor se desejar que seu suplemento do VSTO seja carregado sob demanda. O aplicativo carrega o suplemento do VSTO quando o usuário executa o aplicativo pela primeira vez. Na próxima vez que o usuário executar o aplicativo, o aplicativo carregará todos os elementos da interface do usuário que são definidos pelo suplemento do VSTO, mas o suplemento do VSTO não será carregado até que o usuário clique em um elemento de interface de usuário associado ao suplemento do VSTO.<br /><br /> Quando o aplicativo carrega o suplemento do VSTO com êxito pela primeira vez, o valor **LoadBehavior** permanece 16 enquanto o suplemento do VSTO é carregado. Depois que o aplicativo é fechado, o valor **LoadBehavior** muda para 9.|

## <a name="see-also"></a>Consulte também
- [Arquitetura de soluções do Office no Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Criar soluções do Office](../vsto/building-office-solutions.md)
- [Implantar uma solução do Office](../vsto/deploying-an-office-solution.md)
