{
  "Title": "Langton's Ants in ScalaJS",
  "Pubdate": "2020-03-01",
  "Keywords": [
  ],
  "Tags": [
  ],
  "Slug": "ants",
  "Section": "projects",
  "comments": false
}

{{< rawhtml >}}
<script type="text/javascript" language="javascript" src="/js/scalaants-opt.js"></script>
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAIAAAACACAIAAABMXPacAAABSUlEQVR42u3XQQrAIAxFwdz/0ilUKvYE4cuIIHQXcHi2Knl1d60dPUPoqmPvL3lTZF//99gCIue5RkARMNuA1GEIIEADCCBAAwggQAMIIEADCCBAAwggQAMIIEADCCBAAwggQAMIIEADCCBAAwggQAMIIEADCCBAAwjQAA0gQAM0gAAN0AACNEADCNAADSBAAwggQAMIIEADCCBAAwggQAMIIEADCCBAAwggQAMIIEADCCBAAwgg4DdF8qrv+sdOEi9gHbljXNUAr6DJBhAw/B9AAAEaQAABGkAAARpAAAEaQAABGkAAARpAAAEaQAABGkAAARpAAAEaQAABGkAAARpAAAEaQAABGkAAARpAAAEaQAABGkAAARpAAAEaQAABGkAAARpAAAEaQAABGkAAARpAAAEaQAABGkAAARpAAAEaQAABGkBAvoAH1KryYVgLJK4AAAAASUVORK5CYII=" onclick="AntLib.antPopup('SLSL/SRRR')" alt="SLSL/SRRR" />
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAIAAAACACAIAAABMXPacAAAHFklEQVR42u1d0XLjQAjT//8017k2NpJw47WT3D1op5Np07QP4BVCCyzwdxXqa329YFu1v/P9TWH/QD0Wso7XtwWxWXAz4MOYf1+/3/0xZzPxbuRCe/1xFX7+MD446YPNAT/mfnw15zzsLl5qjuh+qO6kGPrsPtge9G9T9zdLLN52ww5E3THBoqtYhPYjb5Ntg8hDv7mrWz1YdAOLGNjZJ3vs5ZCARygOFr0Eix47oCw0t0e+mBehPfjBohfwoiKOtO8KIkKg3RAsegMv6qZEDZ9rHkIFi165D9pe2L76s19FgFXqgGDRXR/se2GzXX+0oVkCAU6w6L4Ppri8aw8eBoqBKFh00wdTXGZeRBaXaBEsektcBgiIDIuKpaVg0XtyhJaUORaFF71fr9jygwmLwov+CywKL/r3WBRe9I+xKLwovChYFF4UXhQsCi8KLwoWhReFFwWLwovCi4JF4UXhRcGi8KLwomBReFF4UbAovCi8KFgUXhReFCy6x4uq9QzGyB/lRbAW2v23WZ/gRc3o1LAWH3yIF3nnWvHuyXorL9qMLp081Dmb9QFeVMXDFKSTOetdvKj1SxV3kWR9iBe1uRYlExdQ2QRv5kU7QQJ9sHW4lbOmrNfxot4+buRHoSnrlbxoY/09HQN19OuYo3jiVViETvihW0T4j/ggRr6IRTDrow/VwWRl7uyMSnEPizY3GA2FtvdLROapLknQLmIRWkDubtjCgPjDDg98rlrW2X2AA15EAMVZWHfYvjNYyo6R1/aBj6zAOD2qCXMDEeLYHiOf9oEH4WKjtwRt5qYNrPQDWU99oClxP5KUhAC/zF8bBLv4YMUHYG7TVSBDJOFC8/Oes8wVJ3DOJfgzHYepmMTJgYoZWc+DgRu9H0ZO4kRPmOlspw8Ai2R01glyItYNXTxXVpzUpCT9Hix2ZP3mAlH8AT0qaO/0z4sLxQGiOMXOz4OB5mgyUY23i6TNBPqWviUenPJB3xP6BKMkLXBNooqG0HqRXXxwygcyzRo20bps2ibG2bN8eJl9sIhGIgGBNAmHGio0ampS1zmyD67kaODSFcraZNayFJd2jbpS83vTBweK9ChmjEfQKl/HB0t60RH/kRSBql1sNqrfDxIjL+tFEEF0vGwFesBQnM3FB+tyBTBUcR0ck8HMjWNmFR8s7gNmli45lCUHop96chAfLOwDZZkm2Ek24O1/Qmfjg7UEQZlMadmEaKsayWu+Ny0+WAkGkhmYXEqkSO7s4hbM4SNZC24AbwJr5dBeBKvoGleMvBAPhFZKn4HUOsr5mrYjxAd3YrIrprCjNO+F0rt00oy27APrOhb+g6ndjDoD+wcs4Gc98cEvtbqUvmGoPZUMWXLm+GA5Ju/5gWRwfIumKqPQDhzqY4gbzubJGLottcBd7im1A/2jnsD44LkTUHYv71R0NDCivhXGnK7SGXgmGJgw5xJeHTXV+LGzhIEA0cmA7Oyom5uCgWkagwurxgLhrBO7gc8MMB7acLpQVpWtOUfaY5cDQ48QLF/DTwvkD81tGVaxniezDEdIBTu/ZG46kFekD+cSENXBcDono6PO4TAVH1whqToeQXIucCm8qNyl7Ztxw3qKADrSoZMyKwGeukBK+8gTk8+6wDOsxizBHcj9r0pCN3KGc8MHIjN4WbXo0VIXTO/zULX4YMUHVldBORlqFB5cmRAUSjxYZamlKlBpT7KPDREWS0Els9TO5wc19iELNZpSB02qDYiyD1ZyNJGvD3uWSyQ8EuxsiFd40YIPvJ2mrKrXwzURKhxMVcha8AF0SNowyc7PO/3kUpp2spawSFQK0vIYZDCWiEluEW56AYvkqR8C70GFr/ZCpQfkMhbBMq9BTbJRXpC6I5s8nrWCRaU69jDBnUeN28UH6RG/sQ9Qw7jesSpbx7swO0pP4I19UFMLAhcCe09gTUfNyJ1Ed3I0ojqO+6Vts6Jl506i2zkat8rqs++dmmM5cOLBrRzNa7wsJouqAZ+nJj6IH85jkT/gR0Ma9WyAK/WYUGUvrPpgy86AEfeHKe+YZ9tV78+Modf2AYYp+n7mLM0ec31jYsIVXmT9ZRoqhCPRP2IWm7h8kRf1nmTnpvKAW/HE481wozt6EXB05dCQuMkmgLwkV76aox01+FFFhZc77tsiufLtHI3oZqtj1BtZHI40cUhMvoZFk/BZVqsiSGUyauLBPV5E8GJTKHS+BR47AHPlY3xwiRfxnbBl4KOhWxS+xOS7etFUJCEjgEElqtNZT2LyS3K04TRYxiL0eA0eqpOYfBOLhpFoGJpnMd6IlnjwGiw6GHxdLgSRrseTZxMPLmPRzoKmMxxsv56S4yrT7RIPLudoIhmBG6Gg+pEfGiQe3MzR7MLLksYCv2DT/2Ow6DoWeZsZVMG2G+0wFYgFi+5gkZc1ov4A5nUPlwcl8GcAAAAASUVORK5CYII=" onclick="AntLib.antPopup('RLRL/LLLR')" alt="RLRL/LLLR" /> 
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAIAAAACACAIAAABMXPacAAADs0lEQVR42u2d0Y6EIAxF7///NJtsMloKzupGaJVj5sGwO472XEqpVaTfrXw21Vva9qvbwPNRcSem7dOesIp6xwHAf9s/Bu0A+P3ayeMAYJLSARCsdAAEKx0AwUoHQLDSARCs9CUBZFL6egCSKX0xAEqn9JUAKKPSlwFQW78AYCqAxvoAmAigZ30AzAJwYH0ATAFwbH0AjAfw1foAGAzgL+sDYCSAE9YHwDAA56wPgDEATlsfAAMAXLE+AO5uv2h9ANxdh3PR+gC4uQ7nqvUBcH8dztVbMwC4uTqhACC24gwAwRVnAAiuOANAcMUZAIIrzgAQXHEGgOCKs+UBRFecrQQgZW3lMgCy1la+EcATqojfC+AhVcQvBJBc6S8EUHsaJVf62wA0nkbJlf5gAOfG1IeXpaQFcHFMBUBwRgAAwRkBAARnBAAQnBEAQHBGAADBGYF3AtA+zeFdEaMBWGOb727tyXNfjwcgU7friKh4Nrwr4mYAai37sftuZTX/Jt4VcR8A+7d93zgf3w14V8S/21tvr1rXxWhfdjDodpoM9wM2H9pqLGl740wsB3ttsmJvySW4rr+eOUnYXuuoGONv+2r3VbzglOK6Ok9dtT08VXslZ+ta1ChLZhyWP1S3cf51eRd1lCzN0271boOZrWvL9oxtKqBryeGo9gcMxTbqVyNn1QGpC0mrEYKnBHwgcBDgq2myqt8MvbmgHZL6Q0guAHlimy6DvtJrVyNzMX5f1dy4tMNAdCyUKOax6u4nc+x3695RzRLqdNue/GlH3QwxXrq48yBWUTd+cJGoaqPbtITrAfKfODski/3/7geSm4Ltfsl0DpmKD/kSqBqVzQvNt0PS+ddRzG4cSxVoNpPkPUjtJTD8jDpyXpZyDtztB918nA58y7ckhPZOY9N5IQyUeQ6sXmDUiThbr25G3dKLhWwmwMZO8+fGuefAdRLTpTY9A1UD9ZfjVLZIMzd+RjraWtzHmnZYdilTnhMedD+gCmNMyG/zEE8R1jPviKnCUHSQwADAhLIUtTfoATD1nvA2DMwszgWAmxEA4KXFuQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAGBhAPLvzAPAxB/WweO7ABihdJ1emQIAM5TOmvJjALCmPGvKrwGANeVZU34NAKwpz5ryKwJIrvQXAmBN+cjzZ035KKUX1pQPz311Pc0PZkzkG2Deu1kAAAAASUVORK5CYII=" onclick="AntLib.antPopup('SLLL/SLLR')" alt="SLLL/SLLR" /> 
{{< /rawhtml >}}

<!--more-->

A fun demonstration of Langton's Ants and generalized Turnites in ScalaJS

* [GitHub](https://github.com/SimiaCryptus/scalaAnts)
* __[Zoos](https://simiacryptus.github.io/scalaAnts/index.html)__
