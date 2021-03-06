Data Loader
****************************

``DataLoader`` is a required layer of any ``Pipeline``, it provides several methods for loading data from raw text file
and preprocessing data by apply ``TextProcessor`` layer. As mentioned before, default data format of text corpus should
be described as follows:

Polarity first, and text is in following line. Training samples are separated by ``\n\n``.

.. code-block::

    # train.txt
    polarity_01
    sentence_01

    polarity_02
    sentence_02

    ...

    # test.txt
    polarity_01
    sentence_01

    polarity_02
    sentence_02

    ...

.. code-block:: python

    data_loader = DataLoader(text_processor=text_processor)
    data = data_loader(train='train.txt', test='test.txt')

You can set your own ``delimiter`` (separator between polarity and text), ``line_separator`` (separator between samples). For
instance, if ``delimiter='\t'`` and ``line_separator='\n'``, your data should be:

.. code-block::

    # train.txt
    polarity_01     sentence_01
    polarity_02     sentence_02
    ...

    # test.txt
    polarity_01     sentence_01
    polarity_02     sentence_02
    ...

.. code-block:: python

    data_loader = DataLoader(text_processor=text_processor, delimiter='\t', line_separator='\n')
    data = data_loader(train='train.txt', test='test.txt')

``DataLoader`` will return a ``sentivi.data.data_loader.Corpus`` instance when executed.

.. autoclass:: sentivi.data.DataLoader
    :members:

.. toctree::
    :maxdepth: 2

    corpus