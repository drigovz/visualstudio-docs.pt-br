---
title: Acesso do VBA para criar/abrir um projeto de sistema do VSTO
titleSuffix: ''
description: Saiba que você deve habilitar explicitamente o acesso ao sistema de projeto do VBA do Office antes de criar ou abrir um Ferramentas do Visual Studio para o projeto do Office System.
ms.custom: seodec18, SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
f1_keywords:
- vst.project.vbawrongversion
- VST.Project.VBASecurityGenericError
- VST.Project.VBASecurityPermissions
- VST.SelectDocWizard.MissingCOM
- VST.Project.VBASecurityNotSet
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ef68ffccd7a048cd0591ee0bf1aa511fe0489c92
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910514"
---
# <a name="enable-access-to-vba-to-create-or-open-a-visual-studio-tools-for-the-microsoft-office-system-project"></a>Habilitar o acesso ao VBA para criar ou abrir um Ferramentas do Visual Studio para o projeto de sistema Microsoft Office

Você deve habilitar explicitamente o acesso ao sistema de projeto Visual Basic for Applications (VBA) no Microsoft Office antes de poder criar ou abrir um Ferramentas do Visual Studio para o projeto do sistema Microsoft Office.

 Microsoft Office projetos de desenvolvimento exigem acesso ao sistema de projeto do Visual Basic for Applications (VBA) no Microsoft Office Word e no Microsoft Office Excel, mesmo que os projetos não usem Visual Basic for Applications. O suporte em tempo de design de controles em projetos do Visual Basic e C# depende do sistema de projeto do Visual Basic for Applications.

 Alguns vírus de macro do Microsoft Office tentam automatizar o sistema de projeto do Visual Basic for Applications como um meio de propagação. Ao permitir o acesso ao sistema de projeto do Visual Basic for Applications, você remove uma proteção que ajuda a impedir a propagação de vírus de macro. No entanto, a segurança normal de macro permanece ativada, de modo que o nível de segurança da macro e da lista de editores confiáveis que você mantém nos aplicativos do Office determinará se alguma macro é executada ou não em seu computador.

> [!NOTE]
> Isso só se aplica ao computador de desenvolvimento. Os computadores dos usuários finais não precisam dessa opção habilitada para executar soluções do Office.

 É importante observar que desabilitar o acesso ao sistema de projeto do Visual Basic for Applications por conta própria não o protege contra vírus, isso simplesmente ajuda a interromper a disseminação de alguns vírus para outros documentos se o seu computador já estiver infectado com um vírus de macro. A opção é desabilitada por padrão como uma camada adicional de proteção ao computador, mas habilitá-la não torna seu computador mais suscetível a vírus se você estiver seguindo as práticas recomendadas de segurança.

 A melhor proteção contra vírus de macro do Office é executar o Office no nível alto ou muito alto de segurança, para confiar apenas em macros de fontes verificadas, conhecidas e para manter-se atualizado com patches de segurança e scanners de vírus.

 Você pode habilitar ou desabilitar a opção **confiar no acesso para Visual Basic projeto** manualmente.

 Você pode reparar a instalação do Office se vir erros de VBA ou COM.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-enable-or-disable-access-to-visual-basic-projects"></a>Para habilitar ou desabilitar o acesso a projetos Visual Basic

1. Clique na guia **arquivo** .

2. Clique em **Opções**.

3. Clique em **central de confiabilidade** e em **configurações da central de confiabilidade**.

4. Na **central de confiabilidade**, clique em **configurações de macro**.

5. Marque ou desmarque **o acesso de confiança ao modelo de objeto do projeto VBA** para habilitar ou desabilitar o acesso a projetos Visual Basic.

6. Clique em **OK**.

### <a name="to-enable-or-disable-access-to-visual-basic-projects-with-the-2007-microsoft-office-system"></a>Para habilitar ou desabilitar o acesso a projetos Visual Basic com o sistema de Microsoft Office 2007

1. No menu **ferramentas** do Word ou Excel, aponte para **macro** e clique em **segurança**.

2. Na caixa de diálogo **segurança** , clique na guia **editores confiáveis** .

3. Selecione para habilitar ou desmarcar para desabilitar, **confiar no acesso ao Visual Basic projeto**.

4. Clique em **OK**.

## <a name="to-set-your-office-macro-security-level"></a>Para definir o nível de segurança de macro do Office

1. Clique na guia **arquivo** .

2. Clique em **Opções**.

3. Clique em **central de confiabilidade** e em **configurações da central de confiabilidade**.

4. Na **central de confiabilidade**, clique em **configurações de macro**.

5. Na seção **configurações de macro** , selecione a configuração desejada.

6. Clique em **OK**.

### <a name="to-set-your-office-macro-security-level-with-the-2007-microsoft-office-system"></a>Para definir o nível de segurança de macro do Office com o sistema de Microsoft Office de 2007

1. No menu **ferramentas** do Word ou Excel, aponte para **macro** e clique em **segurança**.

2. Na guia **nível de segurança** , selecione a configuração desejada.

    A guia **nível de segurança** contém detalhes sobre cada nível. Para mais informações, consulte o tópico "Níveis de segurança de macro" na Ajuda do Office.

### <a name="to-install-vba-with-the-2007-microsoft-office-system"></a>Para instalar o VBA com o sistema Microsoft Office 2007

1. No painel de controle, execute **Adicionar ou remover programas** ou **programas e recursos**.

2. Selecione Office na lista de **programas instalados atualmente** .

3. Clique em **Alterar**.

4. Selecione **Adicionar ou remover recursos** e clique em **continuar**.

5. Selecione **escolher personalização avançada de aplicativos** e clique em **Avançar**.

6. Expanda **recursos compartilhados do Office** na lista **escolha as opções de atualização para aplicativos e ferramentas** .

7. Abra o menu suspenso ao lado de **Visual Basic for Applications** e, em seguida, clique em **Executar de meu computador**.

8. Clique em **Continue**.

9. Clique em **fechar**

## <a name="to-repair-your-installation-of-office"></a>Para reparar a instalação do Office

1. No painel de controle, execute **Adicionar ou remover programas** ou **programas e recursos**.

2. Selecione sua versão do Office na lista de **programas instalados no momento** .

3. Clique em **Alterar**.

4. Selecione **reinstalar ou reparar** e clique em **Avançar**.

5. Selecione **detectar e reparar erros na instalação do Office** e, em seguida, clique em **instalar**.

## <a name="see-also"></a>Consulte também
- [Proteger soluções do Office](../vsto/securing-office-solutions.md)
