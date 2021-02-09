---
title: Desabilitar o reconhecimento de DPI no Visual Studio
description: Discute as limitações do Designer de Formulários do Windows em monitores de HDPI e como executar o Visual Studio como um processo sem reconhecimento de DPI.
ms.date: 09/28/2020
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.topic: conceptual
ms.openlocfilehash: f63d831127951815f28955e72ae29b1a4d7f5a3e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917098"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a>Desabilitar o reconhecimento de DPI no Visual Studio

O Visual Studio é um aplicativo com reconhecimento de DPI (pontos por polegada), o que significa que a exibição é dimensionada automaticamente. Se um aplicativo indicar que não tem reconhecimento de DPI, o sistema operacional dimensionará o aplicativo como um bitmap. Esse comportamento também é chamado de virtualização de DPI. O aplicativo ainda opera como se estivesse sendo executado em escala de 100% ou 96 dpi.

Este artigo discute as limitações do Designer de Formulários do Windows em monitores de HDPI e como executar o Visual Studio como um processo sem reconhecimento de DPI.

## <a name="windows-forms-designer-on-hdpi-monitors"></a>Designer de Formulários do Windows em monitores de HDPI

O **Designer de Formulários do Windows** no Visual Studio não tem suporte para dimensionamento. Isso causa problemas de exibição ao abrir alguns formulários no **Designer de Formulários do Windows** em monitores de HDPI (altos pontos por polegada). Por exemplo, os controles podem parecer sobrepostos, conforme mostrado na imagem a seguir:

![Designer de Formulários do Windows no monitor de HDPI](./media/win-forms-designer-hdpi.png)

Quando você abre um formulário no **Designer de Formulários do Windows** no Visual Studio em um monitor de HDPI, o Visual Studio exibe uma barra informativa amarela na parte superior do designer:

![barra informativa no Visual Studio para reiniciar no modo sem reconhecimento de DPI](./media/scaling-gold-bar.png)

A mensagem lê o **dimensionamento na exibição principal é definida como 200% (192 DPI). Isso pode causar problemas de renderização na janela do designer.**

> [!NOTE]
> Essa barra informativa foi introduzida no Visual Studio 2017 versão 15.8.

Se não estiver trabalhando no designer e não precisar ajustar o layout do formulário, você poderá ignorar a barra informativa e continuar trabalhando no editor de código ou em outros tipos de designers. (Você também pode [desabilitar notificações](#disable-notifications) para que a barra informativa não continue a aparecer.) Somente o **Designer de formulários do Windows** é afetado. Se você precisar trabalhar no **Designer de Formulários do Windows**, a próxima seção ajudará a [resolver o problema](#to-resolve-the-display-problem).

## <a name="to-resolve-the-display-problem"></a>Para resolver o problema de exibição

Há três opções para resolver o problema de exibição:

- [Reiniciar o Visual Studio como um processo sem reconhecimento de DPI](#restart-visual-studio-as-a-dpi-unaware-process)
- [Adicionar uma entrada de registro](#add-a-registry-entry)
- [Definir a configuração de dimensionamento de exibição como 100%](#set-your-display-scaling-setting-to-100)

> [!TIP]
> Se você preferir gerenciar as configurações da linha de comando, o [`devenv.exe`](../ide/reference/devenv-command-line-switches.md) usa `/noscale` como um parâmetro de linha de comando para ser executado no modo de dimensionamento de 100%.

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a>Reiniciar o Visual Studio como um processo sem reconhecimento de DPI

Você pode reiniciar o Visual Studio como um processo sem reconhecimento de DPI selecionando a opção na barra informativa amarela. Essa é a maneira preferencial de resolver o problema.

Quando o Visual Studio é executado como um processo sem reconhecimento de DPI, os problemas de layout do designer são resolvidos, mas as fontes podem aparecer desfocadas. O Visual Studio exibe uma mensagem informativa amarela diferente quando é executado como um processo sem reconhecimento de DPI que diz que **o Visual Studio está sendo executado como um processo sem reconhecimento de DPI. Designers WPF e XAML podem não ser exibidos corretamente.** A barra informativa também fornece a opção de **Reiniciar o Visual Studio como um processo com reconhecimento de DPI**.

> [!NOTE]
> - Se você tinha janelas de ferramentas desencaixadas no Visual Studio quando selecionou a opção de reiniciar como um processo sem reconhecimento de DPI, a posição dessas janelas de ferramentas poderá ser alterada.
> - Se você usar o perfil padrão do Visual Basic ou se tiver a opção **Salvar novos projetos quando criados** desmarcada em **Ferramentas** > **Opções** > **Projetos e Soluções**, o Visual Studio não poderá reabrir o projeto quando ele for reiniciado como um processo sem reconhecimento de DPI. No entanto, você pode abrir o projeto selecionando-o em **arquivo**  >  **projetos recentes e soluções**.

É importante reiniciar o Visual Studio como um processo com reconhecimento de DPI ao terminar de trabalhar no **Designer de Formulários do Windows.** Quando ele está em execução como um processo sem reconhecimento de DPI, as fontes podem parecer desfocadas e podem ocorrer problemas em outros designers, como o **Designer XAML**. Se você fechar e reabrir o Visual Studio quando ele estiver em execução no modo sem reconhecimento de DPI, ele passará a ser executado novamente com reconhecimento de DPI. Você também pode selecionar a opção **reiniciar o Visual Studio como um processo com reconhecimento de DPI** na barra informativa.

### <a name="add-a-registry-entry"></a>Adicionar uma entrada de registro

Você pode marcar o Visual Studio como um recurso sem reconhecimento de DPI, modificando o registro. Abra o **Editor do Registro** e adicione uma entrada na subchave **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers**:

**Entrada**: dependendo se você estiver usando o Visual Studio 2017 ou 2019, use um destes valores:

- C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe
- C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\devenv.exe

> [!NOTE]
> Se você estiver usando a edição Professional ou Enterprise do Visual Studio, substitua **Community** por **Professional** ou **Enterprise** na entrada. Substitua também a letra da unidade, se necessário.

**Tipo**: REG_SZ

**Valor**: DPIUNAWARE

> [!NOTE]
> O Visual Studio permanecerá no modo sem reconhecimento de DPI até que você remova a entrada do registro.

### <a name="set-your-display-scaling-setting-to-100"></a>Definir a configuração de dimensionamento de exibição como 100%

Para definir a configuração de dimensionamento de exibição como 100% no Windows 10, digite **Configurações de exibição** na caixa de pesquisa da barra de tarefas e, em seguida, selecione **Alterar configurações de exibição**. Na janela **Configurações**, defina **Alterar o tamanho do texto, dos aplicativos e de outros itens** para **100%**.

Definir seu dimensionamento de exibição como 100% pode ser indesejável, pois pode tornar a interface do usuário pequena demais para ser usada.

## <a name="disable-notifications"></a>Desabilitar notificações

Você pode optar por não ser notificado sobre problemas de dimensionamento de DPI no Visual Studio. Talvez você prefira desabilitar as notificações se não estiver trabalhando no designer, por exemplo.

Para desabilitar as notificações, escolha **ferramentas**  >  **Opções** para abrir a caixa de diálogo **Opções** . Em seguida, escolha **Designer de formulários do Windows**  >  **geral** e defina as **notificações de dimensionamento de DPI** como **falso**.

![Opção de notificações de dimensionamento de DPI no Visual Studio](./media/notifications-option.png)

Se, posteriormente, você quiser reabilitar as notificações de dimensionamento, defina a propriedade como **True**.

## <a name="troubleshoot"></a>Solucionar problemas

Se a transição para o reconhecimento de DPI não estiver funcionando conforme o esperado no Visual Studio, verifique se você tem o valor `dpiAwareness` na subchave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\devenv.exe** do Editor do Registro. Exclua o valor se ele estiver presente.

## <a name="see-also"></a>Confira também

- [Dimensionamento automático no Windows Forms](/dotnet/framework/winforms/automatic-scaling-in-windows-forms)
