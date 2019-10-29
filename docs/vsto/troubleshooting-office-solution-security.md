---
title: Solucionar problemas de segurança da solução do Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 289ffc3b5260260c9da8d0ec61e5c79890394802
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985556"
---
# <a name="troubleshoot-office-solution-security"></a>Solucionar problemas de segurança da solução do Office
  Este tópico contém dicas para resolver problemas comuns que podem ser encontrados quando você trabalha com a proteção das soluções do Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>As soluções confiáveis não podem ser instaladas de sites restritos
 Os usuários não poderão instalar uma solução de um local da Web se o site estiver listado na zona sites restritos do Internet Explorer. Isso é verdadeiro mesmo que a solução seja assinada com um certificado confiável.

 A URL do manifesto de implantação pode ser categorizada em uma das cinco zonas:

- Meu Computador

- Internet

- Intranet local

- Sites confiáveis

- Sites restritos

  Se o local do manifesto de implantação tiver sido atribuído à zona de sites restritos, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] não instalará a solução. Se o local for conhecido e puder ser confiável, o usuário poderá remover o local da zona de sites restritos e instalar a solução. Para obter informações sobre como gerenciar zonas, consulte [Configurando editores confiáveis do ClickOnce](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).

## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Não é possível instalar soluções de compartilhamentos de arquivos de rede ou locais da Web quando a configuração de segurança reforçada do Internet Explorer ou o Internet Explorer 7 está
 O Internet Explorer Enhanced Security Configuration (IEESC) no Windows Server 2003 e superior, e no Internet Explorer 7 e superior, restringe significativamente a capacidade dos usuários de navegar pela Internet. Quando os usuários tentam instalar soluções do Office de um compartilhamento de arquivos de rede ou um local da Web, eles podem receber a seguinte mensagem de erro: "a funcionalidade personalizada neste aplicativo não funcionará porque o certificado usado para assinar o manifesto de implantação para *o SolutionName* não é confiável. Contate o administrador para obter assistência adicional. "

 Com o IEESC e o Internet Explorer 7 e superior, se a URL do manifesto de implantação for categorizada na zona da Internet, o manifesto deverá ter um certificado de um fornecedor confiável ou a solução não poderá ser instalada. Sem IEESC, o comportamento padrão é solicitar que o usuário final tome uma decisão de confiança.

 Para gerenciar o efeito do IEESC e do Internet Explorer 7 e superior, identifique sites e caminhos UNC (Convenção de nomenclatura universal) nos quais você confia e adicione-os a uma das zonas de segurança confiáveis (intranet local ou sites confiáveis). Para obter informações sobre como gerenciar zonas, consulte [Configurar editores confiáveis do ClickOnce](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).

## <a name="see-also"></a>Consulte também
- [Proteger soluções do Office](../vsto/securing-office-solutions.md)
