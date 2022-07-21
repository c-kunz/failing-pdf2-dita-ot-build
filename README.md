# Repository to reproduce failing PDF2 build on DITA-OT 3.7.2

## Steps to reproduce

1. `dita -f pdf2 -i repro.dita`

## Expected result

PDF is generated, replacing the missing glyph with literal `#`.

See:

https://xmlgraphics.apache.org/fop/2.6/fonts.html#missing-glyphs

## Actual result

```
      [fop] [ERROR] Anttask - Error rendering fo file: /tmp/temp20220721110741020/topic.fo <org.apache.fop.apps.FOPException: java.util.NoSuchElementException
      [fop] java.util.NoSuchElementException>org.apache.fop.apps.FOPException: java.util.NoSuchElementException
      [fop] java.util.NoSuchElementException
      [fop] 	at org.apache.fop.tools.anttasks.FOPTaskStarter.renderInputHandler(Fop.java:652)
      [fop] 	at org.apache.fop.tools.anttasks.FOPTaskStarter.render(Fop.java:671)
      [fop] 	at org.apache.fop.tools.anttasks.FOPTaskStarter.run(Fop.java:532)
      [fop] 	at org.apache.fop.tools.anttasks.Fop.execute(Fop.java:369)
      [fop] 	at org.apache.tools.ant.UnknownElement.execute(UnknownElement.java:299)
      [fop] 	at jdk.internal.reflect.GeneratedMethodAccessor6.invoke(Unknown Source)
      [fop] 	at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
      [fop] 	at java.base/java.lang.reflect.Method.invoke(Method.java:564)
      [fop] 	at org.apache.tools.ant.dispatch.DispatchUtils.execute(DispatchUtils.java:99)
      [fop] 	at org.apache.tools.ant.Task.perform(Task.java:350)
      [fop] 	at org.apache.tools.ant.Target.execute(Target.java:449)
      [fop] 	at org.apache.tools.ant.Target.performTasks(Target.java:470)
      [fop] 	at org.apache.tools.ant.Project.executeSortedTargets(Project.java:1401)
      [fop] 	at org.apache.tools.ant.helper.SingleCheckExecutor.executeTargets(SingleCheckExecutor.java:36)
      [fop] 	at org.apache.tools.ant.Project.executeTargets(Project.java:1264)
      [fop] 	at org.apache.tools.ant.taskdefs.Ant.execute(Ant.java:437)
      [fop] 	at org.apache.tools.ant.taskdefs.CallTarget.execute(CallTarget.java:106)
      [fop] 	at org.apache.tools.ant.UnknownElement.execute(UnknownElement.java:299)
      [fop] 	at jdk.internal.reflect.GeneratedMethodAccessor6.invoke(Unknown Source)
      [fop] 	at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
      [fop] 	at java.base/java.lang.reflect.Method.invoke(Method.java:564)
      [fop] 	at org.apache.tools.ant.dispatch.DispatchUtils.execute(DispatchUtils.java:99)
      [fop] 	at org.apache.tools.ant.Task.perform(Task.java:350)
      [fop] 	at org.apache.tools.ant.Target.execute(Target.java:449)
      [fop] 	at org.apache.tools.ant.Target.performTasks(Target.java:470)
      [fop] 	at org.apache.tools.ant.Project.executeSortedTargets(Project.java:1401)
      [fop] 	at org.apache.tools.ant.helper.SingleCheckExecutor.executeTargets(SingleCheckExecutor.java:36)
      [fop] 	at org.apache.tools.ant.Project.executeTargets(Project.java:1264)
      [fop] 	at org.apache.tools.ant.taskdefs.Ant.execute(Ant.java:437)
      [fop] 	at org.apache.tools.ant.taskdefs.CallTarget.execute(CallTarget.java:106)
      [fop] 	at org.apache.tools.ant.UnknownElement.execute(UnknownElement.java:299)
      [fop] 	at jdk.internal.reflect.GeneratedMethodAccessor6.invoke(Unknown Source)
      [fop] 	at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
      [fop] 	at java.base/java.lang.reflect.Method.invoke(Method.java:564)
      [fop] 	at org.apache.tools.ant.dispatch.DispatchUtils.execute(DispatchUtils.java:99)
      [fop] 	at org.apache.tools.ant.Task.perform(Task.java:350)
      [fop] 	at org.apache.tools.ant.Target.execute(Target.java:449)
      [fop] 	at org.apache.tools.ant.Target.performTasks(Target.java:470)
      [fop] 	at org.apache.tools.ant.Project.executeSortedTargets(Project.java:1401)
      [fop] 	at org.apache.tools.ant.Project.executeTarget(Project.java:1374)
      [fop] 	at org.apache.tools.ant.helper.DefaultExecutor.executeTargets(DefaultExecutor.java:41)
      [fop] 	at org.apache.tools.ant.Project.executeTargets(Project.java:1264)
      [fop] 	at org.dita.dost.invoker.Main.runBuild(Main.java:694)
      [fop] 	at org.dita.dost.invoker.Main.startAnt(Main.java:211)
      [fop] 	at org.apache.tools.ant.launch.Launcher.run(Launcher.java:284)
      [fop] 	at org.apache.tools.ant.launch.Launcher.main(Launcher.java:101)
      [fop] Caused by: org.apache.fop.apps.FOPException: java.util.NoSuchElementException
      [fop] java.util.NoSuchElementException
      [fop] 	at org.apache.fop.cli.InputHandler.transformTo(InputHandler.java:296)
      [fop] 	at org.apache.fop.cli.InputHandler.renderTo(InputHandler.java:116)
      [fop] 	at org.apache.fop.tools.anttasks.FOPTaskStarter.renderInputHandler(Fop.java:648)
      [fop] 	... 45 more
      [fop] Caused by: java.util.NoSuchElementException
      [fop] 	at java.base/java.util.LinkedHashMap$LinkedHashIterator.nextNode(LinkedHashMap.java:760)
      [fop] 	at java.base/java.util.LinkedHashMap$LinkedValueIterator.next(LinkedHashMap.java:785)
      [fop] 	at org.apache.fop.pdf.PDFFactory.setupFontMetrics(PDFFactory.java:1184)
      [fop] 	at org.apache.fop.pdf.PDFFactory.handleType1CFont(PDFFactory.java:1165)
      [fop] 	at org.apache.fop.pdf.PDFFactory.makeFont(PDFFactory.java:1013)
      [fop] 	at org.apache.fop.pdf.PDFResources.addFonts(PDFResources.java:137)
      [fop] 	at org.apache.fop.render.pdf.PDFDocumentHandler.endDocument(PDFDocumentHandler.java:186)
      [fop] 	at org.apache.fop.render.intermediate.util.IFDocumentHandlerProxy.endDocument(IFDocumentHandlerProxy.java:187)
      [fop] 	at org.apache.fop.render.intermediate.IFRenderer.stopRenderer(IFRenderer.java:295)
      [fop] 	at org.apache.fop.area.RenderPagesModel.endDocument(RenderPagesModel.java:265)
      [fop] 	at org.apache.fop.area.AreaTreeHandler.endDocument(AreaTreeHandler.java:342)
      [fop] 	at org.apache.fop.fo.FOTreeBuilder.endDocument(FOTreeBuilder.java:170)
      [fop] 	at net.sf.saxon.event.ContentHandlerProxy.close(ContentHandlerProxy.java:297)
      [fop] 	at net.sf.saxon.event.ProxyReceiver.close(ProxyReceiver.java:103)
      [fop] 	at net.sf.saxon.event.SequenceNormalizer.close(SequenceNormalizer.java:159)
      [fop] 	at net.sf.saxon.event.ReceivingContentHandler.endDocument(ReceivingContentHandler.java:271)
      [fop] 	at org.apache.xerces.parsers.AbstractSAXParser.endDocument(Unknown Source)
      [fop] 	at org.ditang.relaxng.defaults.RelaxNGDefaultsComponent.endDocument(RelaxNGDefaultsComponent.java:730)
      [fop] 	at org.apache.xerces.xinclude.XIncludeHandler.endDocument(Unknown Source)
      [fop] 	at org.apache.xerces.impl.XMLDocumentScannerImpl.endEntity(Unknown Source)
      [fop] 	at org.apache.xerces.impl.XMLEntityManager.endEntity(Unknown Source)
      [fop] 	at org.apache.xerces.impl.XMLEntityScanner.load(Unknown Source)
      [fop] 	at org.apache.xerces.impl.XMLEntityScanner.skipSpaces(Unknown Source)
      [fop] 	at org.apache.xerces.impl.XMLDocumentScannerImpl$TrailingMiscDispatcher.dispatch(Unknown Source)
      [fop] 	at org.apache.xerces.impl.XMLDocumentFragmentScannerImpl.scanDocument(Unknown Source)
      [fop] 	at org.apache.xerces.parsers.XML11Configuration.parse(Unknown Source)
      [fop] 	at org.ditang.relaxng.defaults.RelaxDefaultsParserConfiguration.parse(RelaxDefaultsParserConfiguration.java:111)
      [fop] 	at org.apache.xerces.parsers.XML11Configuration.parse(Unknown Source)
      [fop] 	at org.apache.xerces.parsers.XMLParser.parse(Unknown Source)
      [fop] 	at org.apache.xerces.parsers.AbstractSAXParser.parse(Unknown Source)
      [fop] 	at org.apache.xerces.jaxp.SAXParserImpl$JAXPSAXParser.parse(Unknown Source)
      [fop] 	at net.sf.saxon.event.Sender.sendSAXSource(Sender.java:439)
      [fop] 	at net.sf.saxon.event.Sender.send(Sender.java:142)
      [fop] 	at net.sf.saxon.jaxp.IdentityTransformer.transform(IdentityTransformer.java:370)
      [fop] 	at org.apache.fop.cli.InputHandler.transformTo(InputHandler.java:293)
      [fop] 	... 47 more
      [fop] 
Error: The following error occurred while executing this line:
/home/kunz/Downloads/dita-ot-3.7.2/plugins/org.dita.pdf2.fop/build_fop.xml:147: [PDFX013F][FATAL] The PDF file '/home/kunz/Desktop/repro/./out/repro.pdf' could not be generated.
```

## Hint

OS: Ubuntu 20.04

Works as expected on DITA-OT 3.6.1

