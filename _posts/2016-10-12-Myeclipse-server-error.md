---
layout: post
title:  "Myeclipse10 server视图报错：Could not create the view: An unexpected exception was thrown.解决"
date:   2016-10-12 19:37:50 +0800 
categories: 编程
tag: myeclipse
---

* content
{:toc}



Myeclipse10 server视图报错
----------


``Could not create the view: An unexpected exception was thrown
java.lang.NullPointerException
	at com.genuitec.eclipse.ast.deploy.core.Deployment.<init>(Unknown Source)
	at com.genuitec.eclipse.ast.deploy.core.ModuleDeployment.<init>(Unknown Source)
	at com.genuitec.eclipse.ast.deploy.core.WebDeployment.<init>(Unknown Source)
	at com.genuitec.eclipse.ast.deploy.core.Deployment.create(Unknown Source)
	at com.genuitec.eclipse.ast.deploy.core.DeploymentManager.loadFromPreferences(Unknown Source)
	at com.genuitec.eclipse.ast.deploy.core.DeploymentManager.init(Unknown Source)
	at com.genuitec.eclipse.ast.deploy.core.DeploymentManager.<init>(Unknown Source)
	at com.genuitec.eclipse.ast.deploy.core.DeploymentManager.getDefault(Unknown Source)
	at com.genuitec.eclipse.ast.deploy.core.ui.ServerTreeViewer$ServerTreeContentProvider.inputChanged(Unknown Source)
	at org.eclipse.jface.viewers.ContentViewer.setInput(ContentViewer.java:276)
	at org.eclipse.jface.viewers.StructuredViewer.setInput(StructuredViewer.java:1690)
	at com.genuitec.eclipse.ast.deploy.core.ui.ServerTreeViewer.<init>(Unknown Source)
	at com.genuitec.eclipse.ast.deploy.core.ui.ServerView.createPartControl(Unknown Source)
	at org.eclipse.ui.internal.ViewReference.createPartHelper(ViewReference.java:375)
	at org.eclipse.ui.internal.ViewReference.createPart(ViewReference.java:229)
	at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:595)
	at org.eclipse.ui.internal.WorkbenchPage$ActivationList.setActive(WorkbenchPage.java:4317)
	at org.eclipse.ui.internal.WorkbenchPage$18.runWithException(WorkbenchPage.java:3359)
	at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(StartupThreading.java:31)
	at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
	at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:135)
	at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:4140)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3757)
	at org.eclipse.ui.application.WorkbenchAdvisor.openWindows(WorkbenchAdvisor.java:803)
	at org.eclipse.ui.internal.Workbench$33.runWithException(Workbench.java:1600)
	at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(StartupThreading.java:31)
	at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
	at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:135)
	at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:4140)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3757)
	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:2609)
	at org.eclipse.ui.internal.Workbench.access$4(Workbench.java:2499)
	at org.eclipse.ui.internal.Workbench$7.run(Workbench.java:679)
	at org.eclipse.core.databinding.observable.Realm.runWithDefault(Realm.java:332)
	at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:668)
	at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:123)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:196)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:344)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:622)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:577)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1410)`





按照搜到的方法

> 打开所在的wordspace文件夹，在下面子文件夹
> .metadata\.plugins\org.eclipse.core.runtime\.settings
> 删除
> com.genuitec.eclipse.ast.deploy.core.prefs
> 即可


试验一无效。
----------


我索性将整个workspace文件夹删除，重启问题依旧。

实验二无效。
----------

最终：
----------

- 删除D盘原有workspace（1.44G）
- 默认在c盘新建workspace
- 删除c盘新建的workspace(1.5G）
- 再打开，正常了

怀疑D盘产生问题，删除后使用默认的c盘workspace，但这个“新建的”C盘workspace其实并不是新建的，很可能是最初就有，我以前改到过D盘，导致该文件夹这么大。

结论
----------


网上分析很有道理，摁着工作空间使劲就行。见一个删一个，失败一个删一个，删删就好了。