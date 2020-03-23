---
title: Inscrições de registro para add-ins VSTO
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
ms.openlocfilehash: b02b50c42692ec2fd455358df5157e0b8481562b
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416517"
---
# <a name="registry-entries-for-vsto-add-ins"></a>Inscrições de registro para add-ins VSTO
  Você deve criar um conjunto específico de entradas de registro ao implantar Add-ins VSTO que são criados usando o Visual Studio. Essas entradas de registro fornecem informações que permitem que o aplicativo do Microsoft Office descubra e carregue o Complemento VSTO.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Quando você constrói seu projeto, o Visual Studio cria essas entradas de registro no computador de desenvolvimento para que você possa facilmente executar e depurar o Add-in VSTO. Se você usar o ClickOnce para implantar o complemento do VSTO, as entradas de registro serão criadas automaticamente no computador do usuário final. Se você usar o Windows Installer para implantar o complemento do VSTO, você deve configurar o projeto InstallShield Limited Edition para criar as entradas de registro no computador do usuário final.

 Para obter mais informações sobre como as entradas de registro são usadas durante o processo de carga para add-ins VSTO, consulte [Arquitetura de Complementos VSTO](../vsto/architecture-of-vsto-add-ins.md).

> [!NOTE]
> Neste tópico, o *ID de complemento de* texto representa um ID exclusivo para o seu Complemento VSTO. Por padrão, o ID é o nome do seu conjunto de complementos VSTO.

## <a name="register-vsto-add-ins-for-the-current-user-vs-all-users"></a>Registre os complementos do VSTO para o usuário atual versus todos os usuários
 Quando um Add-in VSTO é instalado, ele pode ser registrado de duas maneiras:

- Somente para o usuário atual (ou seja, ele está disponível apenas para o usuário que está conectado ao computador quando o Add-in VSTO é instalado). Neste caso, as entradas de registro são criadas o **HKEY_CURRENT_USER**.

- Para todos os usuários (ou seja, qualquer usuário que faça logon no computador pode usar o Add-in VSTO). Neste caso, as entradas de registro são criadas **HKEY_LOCAL_MACHINE**.

  Todos os complementos VSTO que você cria usando o Visual Studio podem ser registrados para o usuário atual. No entanto, os Complementos VSTO podem ser registrados para todos os usuários apenas em determinados cenários. Esses cenários dependem da versão do Microsoft Office no computador e de como o Complemento VSTO foi implantado.

### <a name="deployment-type"></a>Tipo de implantação
 Se você usar o ClickOnce para implantar um Complemento VSTO, o Complemento VSTO pode ser registrado apenas para o usuário atual. Isso porque o ClickOnce só suporta a criação de chaves **HKEY_CURRENT_USER**. Se você quiser registrar um complemento VSTO para todos os usuários em um computador, você deve usar o Windows Installer para implantar o Add-in VSTO. Para obter mais informações sobre esses tipos de implantação, consulte [Implantar uma solução do Office usando o ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md) e implantar uma solução do Office usando o Windows [Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="registry-entries"></a>Entradas do Registro
 As entradas de registro de complemento VSTO necessárias estão localizadas nas seguintes chaves de registro onde *root* é **HKEY_CURRENT_USER** ou **HKEY_LOCAL_MACHINE,** dependendo se a instalação for para o usuário atual ou todos os usuários.

|Aplicação do Escritório|Caminho de configuração|
|------------------|------------------|
|Visio|*Root*\Software\Microsoft\\*Visio*\Addins\\*add-in ID*|
|Todos os outros|*Root*\Software\Microsoft\Office\\Office nome de\\*aplicativo*\Addins*add-in ID*|

> [!NOTE]
> Se o instalador estiver mirando todos os usuários no Windows de 64 bits, recomenda-se que ele inclua duas entradas\\de registro, uma o HKEY_LOCAL_MACHINE\Software\Microsoft e outra o HKEY_LOCAL_MACHINE\Software**WOW6432Node**\Microsoft hive. Isso porque é possível que os usuários usem versões de 32 bits ou 64 bits do Office no computador.
>
>Se o Instalador estiver mirando o usuário atual, ele não precisará ser instalado no WOW6432Node porque o caminho HKEY_CURRENT_USER\Software é compartilhado.
>
>Para obter mais informações, consulte [dados de aplicativos de 32 bits e 64 bits no Registro](/windows/win32/sysinfo/32-bit-and-64-bit-application-data-in-the-registry)

 A tabela a seguir lista as entradas esta chave de registro.

|Entrada|Type|Valor|
|-----------|----------|-----------|
|**Descrição**|REG_SZ|Obrigatórios. Uma breve descrição do complemento VSTO.<br /><br /> Esta descrição é exibida quando o usuário seleciona o Add-in VSTO no painel **Add-Ins** da caixa de diálogo **Opções** no aplicativo Microsoft Office.|
|**Friendlyname**|REG_SZ|Obrigatórios. Um nome descritivo do Add-in VSTO que é exibido na caixa de diálogo **Com Add-Ins** no aplicativo Microsoft Office. O valor padrão é o ID de complemento VSTO.|
|**LoadBehavior**|REG_DWORD|Obrigatórios. Um valor que especifica quando o aplicativo tenta carregar o Complemento VSTO e o estado atual do Complemento VSTO (carregado ou descarregado).<br /><br /> Por padrão, esta entrada é definida como 3, que especifica que o Add-in VSTO está carregado na inicialização. Para obter mais informações, consulte [valores loadBehavior](#LoadBehavior). **Nota:**  Se um usuário desativar o Complemento VSTO, essa ação modifica o valor **do LoadBehavior** na **colmeia de** registro HKEY_CURRENT_USER. Para cada usuário, o valor do valor **LoadBehavior** na colmeia de HKEY_CURRENT_USER substitui o Carregamento Padrão **Configurado** na **colmeia de HKEY_LOCAL_MACHINE.**|
|**Manifesto**|REG_SZ|Obrigatórios. O caminho completo do manifesto de implantação para o Complemento VSTO. O caminho pode ser um local no computador local, um compartilhamento de rede (UNC) ou um servidor Web (HTTP).<br /><br /> Se você usar o Windows Installer para implantar a solução, você deve adicionar o prefixo **file:///** ao caminho **manifesto.** Você também deve anexar a seqüência **&#124;vstolocal** (ou seja, o caractere de tubo **&#124;** seguido por **vstolocal**) até o final deste caminho. Isso garante que sua solução seja carregada a partir da pasta de instalação, em vez do cache ClickOnce. Para obter mais informações, consulte [Implantar uma solução do Office usando o Windows Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md). **Nota:**  Quando você constrói um complemento VSTO no computador de desenvolvimento, o Visual Studio anexa automaticamente a **seqüência vstolocal&#124;** a esta entrada de registro.|

### <a name="registry-entries-for-outlook-form-regions"></a><a name="OutlookEntries"></a>Inscrições de registro para regiões de formulário do Outlook
 Se você criar uma região de formulário personalizada em um complemento do VSTO para o Outlook, entradas adicionais de registro serão usadas para registrar a região do formulário com o Outlook. Essas entradas são criadas uma chave de registro diferente para cada classe de mensagem que a região do formulário suporta. Essas chaves de registro estão no local a seguir, onde *root* é **HKEY_CURRENT_USER** ou **HKEY_LOCAL_MACHINE**.

 *Root*\Software\Microsoft\Office\Outlook\Classe\\*de mensagem* FormRegions

 Como as outras entradas de registro compartilhadas por todos os Complementos do VSTO, o Visual Studio cria as entradas de registro de região do formulário no computador de desenvolvimento quando você constrói seu projeto. Se você usar o ClickOnce para implantar o complemento do VSTO, as entradas de registro serão criadas automaticamente no computador do usuário final. Se você usar o Windows Installer para implantar o complemento do VSTO, você deve configurar o projeto InstallShield Limited Edition para criar as entradas de registro no computador do usuário final.

 Para obter mais informações sobre as entradas de registro da região do formulário, consulte [Especificar a localização de uma região de formulário em um formulário personalizado](/office/vba/outlook/Concepts/Creating-Form-Regions/specify-the-location-of-a-form-region-in-a-custom-form). Para obter mais informações sobre as regiões de formulário do Outlook, consulte [Criar regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md).

## <a name="loadbehavior-values"></a><a name="LoadBehavior"></a>Valores de Comportamento de Carga
 A entrada **LoadBehavior** o*nome*\\de aplicativo *Root*\Software\Microsoft\Office \Addins\\*add-in ID* contém uma combinação bitwise de valores que especificam o comportamento de tempo de execução do Add-in VSTO. O bit de ordem mais baixo (valores 0 e 1) indica se o Add-in VSTO está atualmente descarregado ou carregado. Outros bits indicam quando o aplicativo tenta carregar o complemento VSTO.

 Normalmente, a entrada **LoadBehavior** deve ser definida como 0, 3 ou 16 (em decimal) quando o Add-in VSTO é instalado em computadores do usuário final. Por padrão, o Visual Studio define a entrada **LoadBehavior** do seu Add-in VSTO para 3 quando você o constrói ou publica.

 A tabela a seguir lista todos os valores possíveis da entrada **LoadBehavior.** Algumas descrições nesta tabela referem-se a carregar um Complemento VSTO manualmente ou programáticamente. Para carregar um complemento VSTO manualmente, selecione a caixa de seleção ao lado do Add-in VSTO na caixa de diálogo **COM Add-Ins** no aplicativo. Para carregar um Complemento VSTO programáticamente, defina a <xref:Microsoft.Office.Core.COMAddIn.Connect%2A> propriedade do <xref:Microsoft.Office.Core.COMAddIn> objeto que representa o Complemento VSTO como **true**.

|Valor (em decimal)|Status de complemento VSTO|Comportamento de carga de complemento VSTO|Descrição|
|--------------------------|-------------------------|--------------------------------|-----------------|
|0|Descarregado|Não carregue automaticamente|O aplicativo nunca tenta carregar o Complemento VSTO automaticamente. O usuário pode tentar carregar manualmente o Complemento VSTO, ou o Complemento VSTO pode ser carregado programáticamente.<br /><br /> Se o Complemento DO VSTO for carregado com sucesso, o valor **LoadBehavior** permanecerá 0, mas o status do Complemento VSTO na caixa de diálogo **Add-ins COM** será atualizado para indicar que o Complemento DO VSTO está carregado.|
|1|Carregado|Não carregue automaticamente|O aplicativo nunca tenta carregar o Complemento VSTO automaticamente. O usuário pode tentar carregar manualmente o Complemento VSTO, ou o Complemento VSTO pode ser carregado programáticamente.<br /><br /> Embora a caixa de diálogo **COM Add-ins** inins inininininininininininin in sindica que o Add-in VSTO seja carregado após o início do aplicativo, o Add-in VSTO não é carregado até que seja carregado manualmente ou programáticamente.<br /><br /> Se o aplicativo carregar com sucesso o Complemento VSTO, o valor **LoadBehavior** será alterado para 0 e permanecerá em 0 após o fechamento do aplicativo.|
|2|Descarregado|Carregar na inicialização|O aplicativo não tenta carregar o Complemento VSTO automaticamente. O usuário pode tentar carregar manualmente o Complemento VSTO, ou o Complemento VSTO pode ser carregado programáticamente.<br /><br /> Se o aplicativo carregar com sucesso o Complemento VSTO, o valor **LoadBehavior** será alterado para 3 e permanece em 3 após o fechamento do aplicativo.|
|3|Carregado|Carregar na inicialização|O aplicativo tenta carregar o complemento VSTO quando o aplicativo é iniciado. Este é o valor padrão quando você constrói ou publica um Complemento VSTO no Visual Studio.<br /><br /> Se o aplicativo carregar com sucesso o Complemento VSTO, o valor **LoadBehavior** permanece 3. Se ocorrer um erro ao carregar o Add-in VSTO, o valor **LoadBehavior** será alterado para 2 e permanece em 2 após o fechamento do aplicativo.|
|8|Descarregado|Carga demanda|O aplicativo não tenta carregar o Complemento VSTO automaticamente. O usuário pode tentar carregar manualmente o Complemento VSTO, ou o Complemento VSTO pode ser carregado programáticamente.<br /><br /> Se o aplicativo carregar com sucesso o complemento VSTO, o valor **LoadBehavior** será alterado para 9.|
|9|Carregado|Carga demanda|O Complemento VSTO só será carregado quando o aplicativo o exigir, como quando um usuário clica em um elemento de interface do usuário que usa a funcionalidade no Complemento VSTO (por exemplo, um botão personalizado na Fita).<br /><br /> Se o aplicativo carregar com sucesso o Complemento VSTO, o valor **LoadBehavior** permanece 9, mas o status do Add-in VSTO na caixa de diálogo **Add-ins COM** será atualizado para indicar que o Complemento DO VSTO está carregado no momento. Se ocorrer um erro ao carregar o Complemento VSTO, o valor **LoadBehavior** será alterado para 8.|
|16|Carregado|Carregar primeira vez, em seguida, carregar demanda|Defina esse valor se quiser que seu Complemento VSTO seja carregado demanda. O aplicativo carrega o Complemento VSTO quando o usuário executa o aplicativo pela primeira vez. Da próxima vez que o usuário executa o aplicativo, o aplicativo carrega quaisquer elementos de Interface do Usuário definidos pelo Add-in VSTO, mas o Add-in VSTO não é carregado até que o usuário clique em um elemento de interface do usuário associado ao Complemento VSTO.<br /><br /> Quando o aplicativo carrega com sucesso o Complemento VSTO pela primeira vez, o valor **LoadBehavior** permanece 16 enquanto o Complemento VSTO é carregado. Após o fechamento do aplicativo, o valor **LoadBehavior** muda para 9.|

## <a name="see-also"></a>Confira também
- [Arquitetura de soluções de Office no Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Construir soluções do Office](../vsto/building-office-solutions.md)
- [Implantar uma solução de Office](../vsto/deploying-an-office-solution.md)
 