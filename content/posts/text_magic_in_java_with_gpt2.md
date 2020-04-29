{
  "disqus_url": "http://blog.simiacryptus.com/blog/text_magic_in_java_with_gpt2/",
  "disqus_title": "Text Magic in Java with GPT-2",
  "Title": "Text Magic in Java with GPT-2",
  "Pubdate": "2019-05-25",
  "Keywords": [
    "NLP",
    "TensorFlow"
  ],
  "Tags": [
    "NLP",
    "TensorFlow"
  ],
  "Slug": "text_magic_in_java_with_gpt2",
  "Section": "post",
  "comments": true
}

Recently the OpenAI team [made news again](https://openai.com/blog/better-language-models/) by releasing a 335-million parameter pre-trained natural language model. This model, using Python and TensorFlow , can generate text based on preceding text with such impressive capabilities that is can be used to translate and answer questions. This team actually has models several times larger, but have not yet released them due to risks of abuse.

Today I have [released my small contribution](https://github.com/SimiaCryptus/tf-gpt-2) to this awesome project - A deployable TensorFlow model and Java-based reference implementation which uses only the core (i.e. non-python) api and a fully serialized model to perform the same task. These awesome capabilities can now be imported into Java applications with a simple, standard dependency. (Fine print: The 1.2Gb model is also required, though the library makes it easy to download.)

One of the great things about TensorFlow is that it provides a platform for developing neural networks that can be used, theoretically, anywhere. On a server, on your phone, or in your browser; in Python, C, JavaScript, Go, or any other language. However, some TensorFlow functionality is actually written in Python, and many applications also use python for their own logic. Thus, many TensorFlow applications, including GPT-2, are still dependent on Python.

Getting GPT-2 to work outside of Python TensorFlow required solving several challenges. The largest challenge is that the pre-trained model, as published, provided only saved session variables and the python definition code. An [export script](https://github.com/SimiaCryptus/gpt-2/blob/master/export_model.py) was developed in Python to generate a protobuf-formatted graph definition with the pre-trained weights checkpoint loaded - This format is how TensorFlow networks are packaged for deployment. Unfortunately, this model is defined in loop code which actually defines two different variations of the same graph, so to get it working from a static graph definition took a [strange approach](https://github.com/SimiaCryptus/tf-gpt-2/blob/master/src/main/java/com/simiacryptus/text/gpt2/GPT2Edit_345M.java) I won’t delve into here. The second main challenge was to reproduce the logic that invokes the graph, and the logic that encodes/decodes text to the coding scheme used by the model.

This project adds to my existing integrations with TensorFlow which were developed to import the inception vision network. In all I have demonstrated fairly complete integration in Java with the TensorFlow package, including:

1. Importing a TensorFlow model
1. Extracting graph information such as root nodes
1. Writing TensorFlow outputs and launching TensorBoard
1. Differentiating using TensorFlow
1. Various utility functions
1. Extracting graphs into MindsEye models (e.g. for differentiation not yet supported in core TensorFlow)

It is my pleasure to bring these natural language processing tools to the Java community. I hope that many creative applications are explored. However, if you have the capability to wield such technology, if fate has granted you such talent and opportunity, you have a responsibility to humanity to consider the greater good. Technology, as disruptive and irreverent as it is, has a duty to serve humanity.
