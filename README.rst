Xunit parser
============

Xunit parser Provides common interface for different formats of Xunit XML.

Usage
-----


Regardless of whether there are multiple test suites, the library always wraps the results in a TestSuites object

    >>> test_suites = XunitParser().parse('my.xml')
    >>> for test_suite in test_suites.test_suites:
            for test_case in test_suite.test_cases:
                print(test_case)


Xunit parser can also be used in situations where XML must be safely processed from untrusted sources.

For example, you can use Xunit Parser in conjunction with the excellent `defusedxml`: 

    >>> import defusedxml
    >>> test_suites = XunitParser(elementree_class=defusedxml.ElementTree).parse('my.xml')