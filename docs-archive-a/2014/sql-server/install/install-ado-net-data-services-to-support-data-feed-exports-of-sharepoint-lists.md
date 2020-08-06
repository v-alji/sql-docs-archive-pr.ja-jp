---
title: SharePoint リストのデータフィードのエクスポートをサポートするために ADO.NET Data Services をインストールする |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: f32527ae-f623-4e08-adfb-6d3262f5c2ac
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: fb47804daee38427f48baefdf3997edda5fb90b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634229"
---
# <a name="install-adonet-data-services-to-support-data-feed-exports-of-sharepoint-lists"></a><span data-ttu-id="58af0-102">SharePoint リストのデータ フィードのエクスポートをサポートする ADO.NET Data Services のインストール</span><span class="sxs-lookup"><span data-stu-id="58af0-102">Install ADO.NET Data Services to support data feed exports of SharePoint lists</span></span>
  <span data-ttu-id="58af0-103">ADO.NET Data Services は、SharePoint リストのデータ フィードのエクスポートに必要です。</span><span class="sxs-lookup"><span data-stu-id="58af0-103">ADO.NET Data Services is required for a data feed export of SharePoint lists.</span></span> <span data-ttu-id="58af0-104">SharePoint 2010 では、このコンポーネントは SharePoint の必須コンポーネントのインストーラー プログラムに含まれていないため、手動でインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="58af0-104">SharePoint 2010 does not include this component in the SharePoint Prerequisite Installer program, so you must install it manually.</span></span>  
  
 <span data-ttu-id="58af0-105">この前提条件なしで、データ フィードとしてエクスポートされた SharePoint リストの使用を試みると、次のエラーが表示されます。"セキュリティ上の理由から、この XML 文書での DTD 処理は禁止されています。</span><span class="sxs-lookup"><span data-stu-id="58af0-105">Without this prerequisite, you will get the following error when you attempt to use a SharePoint list that was exported as a data feed: "For security reasons DTD is prohibited in this XML document.</span></span> <span data-ttu-id="58af0-106">XmlReaderSettings の ProhibitDtd プロパティを false に設定し、その設定を XmlReader.Create メソッドに渡してください。"</span><span class="sxs-lookup"><span data-stu-id="58af0-106">To enable DTD processing set the ProhibitDtd property on XmlReaderSettings to false and pass the settings into XmlReader.Create method."</span></span>  
  
 <span data-ttu-id="58af0-107">次の手順に従って、リストをデータ フィードとしてエクスポートできるようにする各 SharePoint サーバーに ADO.NET Data Services をインストールします。</span><span class="sxs-lookup"><span data-stu-id="58af0-107">Use the following instructions to install ADO.NET Data Services on every SharePoint server for which you want to allow lists to be exported as data feeds.</span></span>  
  
### <a name="download-and-install-adonet-data-services"></a><span data-ttu-id="58af0-108">ADO.NET Data Services のダウンロードとインストール</span><span class="sxs-lookup"><span data-stu-id="58af0-108">Download and install ADO.NET Data Services</span></span>  
  
1.  <span data-ttu-id="58af0-109">SharePoint 2010 のハードウェアとソフトウェアの要件に関するドキュメント「[ハードウェアとソフトウェアの要件 (sharepoint 2010)](https://go.microsoft.com/fwlink/?LinkId=169734) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58af0-109">Go to the hardware and software requirements documentation for SharePoint 2010, [Hardware and Software Requirements (SharePoint 2010)](https://go.microsoft.com/fwlink/?LinkId=169734)</span></span>  
  
2.  <span data-ttu-id="58af0-110">[**適用可能なソフトウェアへのアクセス**] で、使用しているオペレーティングシステム (windows SERVER 2008 SP2 または windows Server 2008 R2) に対応する ADO.NET Data Services 3.5 のリンクを見つけます。</span><span class="sxs-lookup"><span data-stu-id="58af0-110">In **Access to applicable software**, find the link for ADO.NET Data Services 3.5 that corresponds to the operating system you are using (either Windows Server 2008 SP2 or Windows Server 2008 R2).</span></span>  
  
3.  <span data-ttu-id="58af0-111">リンクをクリックし、サービスをインストールするセットアップ プログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="58af0-111">Click the link and run the setup program that installs the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58af0-112">参照</span><span class="sxs-lookup"><span data-stu-id="58af0-112">See Also</span></span>  
 [<span data-ttu-id="58af0-113">PowerPivot for SharePoint 2010 のインストール</span><span class="sxs-lookup"><span data-stu-id="58af0-113">PowerPivot for SharePoint 2010 Installation</span></span>](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
