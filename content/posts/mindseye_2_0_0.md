{
  "disqus_url": "http://blog.simiacryptus.com/blog/mindseye_2.0/",
  "disqus_title": "MindsEye 2.0",
  "Title": "MindsEye 2.0",
  "Pubdate": "2020-04-26",
  "Keywords": [
    "MindsEye"
  ],
  "Tags": [
    "MindsEye"
  ],
  "Slug": "mindseye_2.0",
  "Section": "post",
  "thumbnail": "http://examples.deepartist.org/img/42dab251-3516-4e7e-88ba-d8512778905e.gif",
  "comments": true
}

Hello Everybody!

Today I'd like to announce the [2.0.0 release](http://code.simiacrypt.us/release/2.0.0/all-projects/) of MindsEye and related projects!

It's been quite a journey already...

<!--more-->

{{< rawhtml >}}
<p>
    <script src="https://simiacryptus.s3.us-west-2.amazonaws.com/descent-animator-opt.js" type="text/javascript"></script>
    <div>
    <canvas height="800" id="canvas_1f62" style="display: block;" width="800"></canvas>
      <script>
        var descent = new Descent(800, 800);
        descent.stepZoom = 0.5;
        descent.animate(document.getElementById('canvas_1f62'),
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/d13e9391-36e4-4f58-aed7-d0ae8fb93a4c.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/ecf9217a-4be4-4798-8707-0823a42e9b19.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/948ac098-a52e-4d51-a212-8f565ae76275.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/1139a529-d0fe-4e5b-8a48-59cd1c728b30.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/8b717d08-e175-45f6-a61c-a374b71d4258.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/569f9faa-1445-410f-8422-96b60863dfd4.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/ee83fca0-67e8-4beb-8528-5e7a5be6ffa5.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/789189ae-ced5-41b2-8822-eb07f5e3c887.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/f8581b7f-b4c4-42de-9dd3-44e4fa043c3e.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/b9b98d27-cf52-4682-b8c4-b08415073722.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/4bbfb7e2-3b09-4afc-80c1-09f163d8efe7.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/cc1935bb-9475-46c7-a8ce-a46850308a37.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/e34ebf54-912c-4440-9ab2-720579aadac1.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/542ea126-0964-4e34-90e0-fb3b145d560c.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/43040c59-5a84-4329-8b98-07bf56c7461b.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/87b50bd0-a318-449d-b61a-80b20d6a82e8.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/6ca7c5d1-0891-47be-8c42-58d982a0c5b6.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/c2bae4e0-96a9-4a1b-b557-0d4d06a4f3b3.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/58aaecb1-2b66-4413-bc7a-915db25b0d0c.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/b5e0ec8b-8177-496f-b9dc-21d34e861464.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/825c74ed-d475-4f46-bada-2561146207d6.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/67e75c25-8913-4a53-b2d6-e18b2dbe9b87.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/88bb321c-f854-408d-9feb-e4ea45e45b84.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/d154bae0-247f-4178-ade2-30841c267c28.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/8a77425f-787d-4656-b018-5341284386a8.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/f3351e3c-8c6c-4430-8560-58d4fd282ede.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/fd67437c-6658-449d-8a7e-70b6b16fe18c.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/f7958ff6-4437-4e8c-a561-4e69fd16b583.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/93eeceae-8229-4e06-a982-9406429448eb.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/226d58f5-f7fe-4034-b8d0-2c2ff5742f39.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/041baa4b-06d6-4000-aad5-23eacf96be30.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/71bf8e95-36fe-426b-a46b-5d9aa9730cd9.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/38d1bf7e-a805-4ed3-8ad0-b74f894ce1d0.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/921542d7-7c7c-40ff-a07e-99c935e5fd44.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/f1228099-30d0-4079-851c-5b9966250254.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/06948c5d-d93a-498f-8de3-fd0a74b9cc46.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/9df5e314-2863-44e6-882f-08b04bcf2d51.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/e54b1c68-6ca8-405a-b384-2dd07e3debe7.jpg',
   'http://examples.deepartist.org/ZoomingRotor/913504f4-304e-4685-80de-259ecb5d87a8/etc/856d926e-2470-4a3e-8e28-410c791c1e3b.jpg');
    </script>
    </div>    
</p>
{{< /rawhtml >}}

Neat, Huh? This type of rendering is my newest addition to deepartist.org - It generates an animation based on several key frames in a symmetric pattern, both of which use the same style-defining network. The final images are animated by a script written in ScalaJS, which is a whole other topic.

This animation isn’t the only new thing I have working - I am just wrapping up many months of reworking code at a pretty deep level (things were not even close to working!) I’ve finally released MindsEye 2.0.0. The biggest change here was introducing [a coding tool](https://github.com/SimiaCryptus/java-reference-counter) which uses automated code analysis to verify reference counting memory management. This change touched the majority of files/methods/lines, but in theory was nonfunctional. It converted previously hand-coded reference counting code into a more rigorous pattern for which static code analysis can be applied. This change will allow easier management of a large code base, as general reference management can be checked by static code analysis and integration testing can be verified by logging interception. This code analysis isn’t perfect and must go along with runtime event log monitoring to prevent memory leaks, but it does make it a lot easier to code!

[The 2.0 release](http://code.simiacrypt.us/release/2.0.0/all-projects/) has several other improvements as well. One of the most obvious is better HTML output for markdown rendering via frontmatter. This has been enhanced with the latest version, with needed javascript libraries for several neat features including code formatting, graphs, and collapsing sections. Also, the testing has been converted to JUnit 5 and heavily restructured. Both the unit tests and the release build are now packaged as [tasks that can be run on an EC2 node](http://code.simiacrypt.us/tests/runner/20200416023252/2000393139_fb04374b-a3f9-43d8-bf9e-6fb113a9a67f/2000393139_fb04374b-a3f9-43d8-bf9e-6fb113a9a67f.html), and the test results are scanned and [reported on in a second process](http://code.simiacrypt.us/tests/com/simiacryptus/mindseye/index/BasicTestReport.html). The unit test [executor](https://github.com/SimiaCryptus/mindseye-cudnn/blob/a84aa7ce8ec0148611860c920e29778fb7d7a65a/src/test/java/com/simiacryptus/mindseye/test/RemoteTests_CuDNN.java#L42) can even isolate tests by method or class in separate jvms.

In general, these developments have a cloud-based theme: All tests, applications, and builds can now be run on EC2, with all important storage on S3. S3 is also an important data buffer, since it is used to store individual test results and then summarize them in aggregate reports. Although a cloud-centric design has many benefits, the main goal I was trying to solve was scale: I want to make this project something that wouldn’t be prohibitively complex for 1) features to be added, or 2) others to contribute. This meant making it easier to develop new code, easier to validate new code for inclusion in a PR, and easier to manage tests and builds. I knew 6 months ago I could not expect anybody else to make a significant contribution to MindsEye due to reference counting code development and special testing concerns; now it is at least a possibility.

This was a huge code change - most files and interfaces were updated, and the core patterns used in reference management were completely replaced. Also, the project structure changed as we moved from Data-Science-Tools to [All-Projects](https://github.com/SimiaCryptus/all-projects/tree/master/) as our umbrella repo. Fortunately, due to a large amount of current layer tests, we have a good deal of validation that major functionality was preserved on the vast majority of code.

We did have some [interesting new eye-candies](http://code.simiacrypt.us/demo/demo_descent.html) to show off since our last release, of course. I’ve improved the rotationally-symmetric renderings to produce a zooming effect, which loops to produce an ad-infinitem effect, previously linked. This is initially previewed as animated GIFs, but is also finally rendered as a very smooth javascript animation.



{{< rawhtml >}}
<p>
Click an ant below to view in detail:<br/>
<script type="text/javascript" language="javascript" src="/js/scalaants-opt.js"></script>
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAIAAAACACAIAAABMXPacAAABSUlEQVR42u3XQQrAIAxFwdz/0ilUKvYE4cuIIHQXcHi2Knl1d60dPUPoqmPvL3lTZF//99gCIue5RkARMNuA1GEIIEADCCBAAwggQAMIIEADCCBAAwggQAMIIEADCCBAAwggQAMIIEADCCBAAwggQAMIIEADCCBAAwjQAA0gQAM0gAAN0AACNEADCNAADSBAAwggQAMIIEADCCBAAwggQAMIIEADCCBAAwggQAMIIEADCCBAAwgg4DdF8qrv+sdOEi9gHbljXNUAr6DJBhAw/B9AAAEaQAABGkAAARpAAAEaQAABGkAAARpAAAEaQAABGkAAARpAAAEaQAABGkAAARpAAAEaQAABGkAAARpAAAEaQAABGkAAARpAAAEaQAABGkAAARpAAAEaQAABGkAAARpAAAEaQAABGkAAARpAAAEaQAABGkBAvoAH1KryYVgLJK4AAAAASUVORK5CYII=" onclick="AntLib.antPopup('SLSL/SRRR')" alt="SLSL/SRRR" /> <img src="data:image/png;base64,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" onclick="AntLib.antPopup('RLRL/LLLR')" alt="RLRL/LLLR" /> <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAIAAAACACAIAAABMXPacAAADs0lEQVR42u2d0Y6EIAxF7///NJtsMloKzupGaJVj5sGwO472XEqpVaTfrXw21Vva9qvbwPNRcSem7dOesIp6xwHAf9s/Bu0A+P3ayeMAYJLSARCsdAAEKx0AwUoHQLDSARCs9CUBZFL6egCSKX0xAEqn9JUAKKPSlwFQW78AYCqAxvoAmAigZ30AzAJwYH0ATAFwbH0AjAfw1foAGAzgL+sDYCSAE9YHwDAA56wPgDEATlsfAAMAXLE+AO5uv2h9ANxdh3PR+gC4uQ7nqvUBcH8dztVbMwC4uTqhACC24gwAwRVnAAiuOANAcMUZAIIrzgAQXHEGgOCKs+UBRFecrQQgZW3lMgCy1la+EcATqojfC+AhVcQvBJBc6S8EUHsaJVf62wA0nkbJlf5gAOfG1IeXpaQFcHFMBUBwRgAAwRkBAARnBAAQnBEAQHBGAADBGYF3AtA+zeFdEaMBWGOb727tyXNfjwcgU7friKh4Nrwr4mYAai37sftuZTX/Jt4VcR8A+7d93zgf3w14V8S/21tvr1rXxWhfdjDodpoM9wM2H9pqLGl740wsB3ttsmJvySW4rr+eOUnYXuuoGONv+2r3VbzglOK6Ok9dtT08VXslZ+ta1ChLZhyWP1S3cf51eRd1lCzN0271boOZrWvL9oxtKqBryeGo9gcMxTbqVyNn1QGpC0mrEYKnBHwgcBDgq2myqt8MvbmgHZL6Q0guAHlimy6DvtJrVyNzMX5f1dy4tMNAdCyUKOax6u4nc+x3695RzRLqdNue/GlH3QwxXrq48yBWUTd+cJGoaqPbtITrAfKfODski/3/7geSm4Ltfsl0DpmKD/kSqBqVzQvNt0PS+ddRzG4cSxVoNpPkPUjtJTD8jDpyXpZyDtztB918nA58y7ckhPZOY9N5IQyUeQ6sXmDUiThbr25G3dKLhWwmwMZO8+fGuefAdRLTpTY9A1UD9ZfjVLZIMzd+RjraWtzHmnZYdilTnhMedD+gCmNMyG/zEE8R1jPviKnCUHSQwADAhLIUtTfoATD1nvA2DMwszgWAmxEA4KXFuQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAGBhAPLvzAPAxB/WweO7ABihdJ1emQIAM5TOmvJjALCmPGvKrwGANeVZU34NAKwpz5ryKwJIrvQXAmBN+cjzZ035KKUX1pQPz311Pc0PZkzkG2Deu1kAAAAASUVORK5CYII=" onclick="AntLib.antPopup('SLLL/SLLR')" alt="SLLL/SLLR" /> 
</p>
{{< /rawhtml >}}

The Javascript library powering that animation is implemented in Scala JS, which I’ve found to be pretty cool. I’ve even implemented in a fairly short time a port of my [previously GWT-powered langton ants](/blog/langtons_ant_and_freinds/), which I’ve now [published in improved form](https://github.com/SimiaCryptus/scalaAnts). In general it felt a lot more lightweight than GWT - I could use the Scala language and usual platform classes, but for UI I was accessing the DOM through a thin wrapper class which felt more direct and transparent.

Partially inspired by the recent release of [OpenAI Microscope](https://openai.com/blog/microscope/), I created a variety of notebooks which highlight the activity of a single neuron at a time in renderings. (These can be viewed at [examples.deepartist.org](http://examples.deepartist.org/)) This can either be iterated over in arbitrary numeric order, or sorted by how closely they match a given image. 

![](/img/e943b3b3-ea57-450d-b405-ef3984e8df76.gif)

These single-neuron patterns can make an interesting base to select from when making new works, as some of these infinitely zooming animations. I think there is a funny similarity between the thumbnails of these ants and the results of the neuron surveys - both display an interesting variety of forms, like biological samples to be cataloged. I hope you have as much fun exploring them as I have had!
