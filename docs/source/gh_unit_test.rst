****************************
Github Action Unit Tests
****************************

A sample template for automating unit tests on Github:

.. code:: yaml

   name: advection-unit-tests

   on: push

   jobs:
    advection-tests:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
        with:
           fetch-depth: 0
 
      - name: Install dependencies
        run: |
           sudo apt-get update -y -qq
           sudo apt-get -qq -y install g++>=9.3.0

      - name: Build
        run: |
            cd one_d_advection
            make unit_test DEBUG=TRUE

      - name: Test
        run: |
            one_d_advection/./unit_test
