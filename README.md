# Bug: useAmp from Next.js breaks auto-imports for TypeScript

* [Issue](https://github.com/zeit/next.js/issues/9436)
* [Screencast](https://youtu.be/7Wbh7WgZNgg)

## TypeScript Trace

```log
[Trace  - 23:39:35] <semantic> Sending request: quickinfo (121). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "line": 3,
    "offset": 19
}
[Trace  - 23:39:35] <semantic> Response received: quickinfo (121). Request took 5 ms. Success: true
Result: {
    "kind": "",
    "kindModifiers": "",
    "start": {
        "line": 3,
        "offset": 16
    },
    "end": {
        "line": 3,
        "offset": 20
    },
    "displayString": "any",
    "documentation": "",
    "tags": []
}
[Trace  - 23:39:35] <semantic> Sending request: quickinfo (122). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "line": 3,
    "offset": 19
}
[Trace  - 23:39:35] <semantic> Response received: quickinfo (122). Request took 2 ms. Success: true
Result: {
    "kind": "",
    "kindModifiers": "",
    "start": {
        "line": 3,
        "offset": 16
    },
    "end": {
        "line": 3,
        "offset": 20
    },
    "displayString": "any",
    "documentation": "",
    "tags": []
}
[Trace  - 23:39:35] <semantic> Sending request: getCodeFixes (123). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "startLine": 3,
    "startOffset": 16,
    "endLine": 3,
    "endOffset": 20,
    "errorCodes": [
        2304
    ]
}
[Trace  - 23:39:35] <semantic> Response received: getCodeFixes (123). Request took 5 ms. Success: false . Message: Error processing request. Debug Failure.
Error: Debug Failure.
    at Object.assertDefined (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:2101:24)
    at getDefaultExportInfoWorker (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:118907:80)
    at getDefaultLikeExportInfo (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:118867:24)
    at /Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:118850:35
    at /Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:119023:21
    at forEachExternalModule (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:119036:21)
    at forEachExternalModuleToImportFrom (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:119021:13)
    at getExportInfos (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:118848:13)
    at getFixesInfoForNonUMDImport (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:118834:57)
    at getFixesInfo (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:118772:50)
    at Object.getCodeActions (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:118533:28)
    at /Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:115852:121
    at Object.flatMap (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:583:25)
    at Object.getFixes (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:115852:23)
    at /Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:125866:35
    at Object.flatMap (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:583:25)
    at Object.getCodeFixesAtPosition (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:125864:23)
    at IOSession.Session.getCodeFixes (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:135063:64)
    at Session.handlers.ts.createMapFromTemplate._a.<computed> (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:133850:61)
    at /Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:135256:88
    at IOSession.Session.executeWithRequestId (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:135247:28)
    at IOSession.Session.executeCommand (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:135256:33)
    at IOSession.Session.onMessage (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:135279:35)
    at Interface.<anonymous> (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:136594:27)
    at Interface.emit (events.js:200:13)
    at Interface._onLine (readline.js:314:10)
    at Interface._normalWrite (readline.js:459:12)
    at Socket.ondata (readline.js:170:10)
    at Socket.emit (events.js:200:13)
    at addChunk (_stream_readable.js:294:12)
    at readableAddChunk (_stream_readable.js:275:11)
    at Socket.Readable.push (_stream_readable.js:210:10)
    at Pipe.onStreamRead (internal/stream_base_commons.js:166:17)
[Trace  - 23:39:37] <semantic> Sending request: quickinfo (124). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "line": 3,
    "offset": 17
}
[Trace  - 23:39:37] <semantic> Response received: quickinfo (124). Request took 2 ms. Success: true
Result: {
    "kind": "",
    "kindModifiers": "",
    "start": {
        "line": 3,
        "offset": 16
    },
    "end": {
        "line": 3,
        "offset": 20
    },
    "displayString": "any",
    "documentation": "",
    "tags": []
}
[Trace  - 23:39:37] <semantic> Sending request: quickinfo (125). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "line": 3,
    "offset": 18
}
[Trace  - 23:39:37] <semantic> Response received: quickinfo (125). Request took 1 ms. Success: true
Result: {
    "kind": "",
    "kindModifiers": "",
    "start": {
        "line": 3,
        "offset": 16
    },
    "end": {
        "line": 3,
        "offset": 20
    },
    "displayString": "any",
    "documentation": "",
    "tags": []
}
[Trace  - 23:39:37] <semantic> Sending request: getCodeFixes (126). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "startLine": 3,
    "startOffset": 16,
    "endLine": 3,
    "endOffset": 20,
    "errorCodes": [
        2304
    ]
}
[Trace  - 23:39:37] <semantic> Response received: getCodeFixes (126). Request took 3 ms. Success: false . Message: Error processing request. Debug Failure.
Error: Debug Failure.
    at Object.assertDefined (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:2101:24)
    at getDefaultExportInfoWorker (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:118907:80)
    at getDefaultLikeExportInfo (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:118867:24)
    at /Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:118850:35
    at /Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:119023:21
    at forEachExternalModule (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:119036:21)
    at forEachExternalModuleToImportFrom (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:119021:13)
    at getExportInfos (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:118848:13)
    at getFixesInfoForNonUMDImport (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:118834:57)
    at getFixesInfo (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:118772:50)
    at Object.getCodeActions (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:118533:28)
    at /Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:115852:121
    at Object.flatMap (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:583:25)
    at Object.getFixes (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:115852:23)
    at /Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:125866:35
    at Object.flatMap (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:583:25)
    at Object.getCodeFixesAtPosition (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:125864:23)
    at IOSession.Session.getCodeFixes (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:135063:64)
    at Session.handlers.ts.createMapFromTemplate._a.<computed> (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:133850:61)
    at /Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:135256:88
    at IOSession.Session.executeWithRequestId (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:135247:28)
    at IOSession.Session.executeCommand (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:135256:33)
    at IOSession.Session.onMessage (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:135279:35)
    at Interface.<anonymous> (/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/typescript/lib/tsserver.js:136594:27)
    at Interface.emit (events.js:200:13)
    at Interface._onLine (readline.js:314:10)
    at Interface._normalWrite (readline.js:459:12)
    at Socket.ondata (readline.js:170:10)
    at Socket.emit (events.js:200:13)
    at addChunk (_stream_readable.js:294:12)
    at readableAddChunk (_stream_readable.js:275:11)
    at Socket.Readable.push (_stream_readable.js:210:10)
    at Pipe.onStreamRead (internal/stream_base_commons.js:166:17)
[Trace  - 23:39:50] <semantic> Sending request: getApplicableRefactors (127). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "startLine": 1,
    "startOffset": 1,
    "endLine": 1,
    "endOffset": 1
}
[Trace  - 23:39:50] <semantic> Response received: getApplicableRefactors (127). Request took 10 ms. Success: true
Result: []
[Trace  - 23:39:50] <syntax> Sending request: getOutliningSpans (62). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx"
}
[Trace  - 23:39:50] <syntax> Response received: getOutliningSpans (62). Request took 2 ms. Success: true
Result: [
    {
        "textSpan": {
            "start": {
                "line": 3,
                "offset": 26
            },
            "end": {
                "line": 6,
                "offset": 2
            }
        },
        "hintSpan": {
            "start": {
                "line": 3,
                "offset": 21
            },
            "end": {
                "line": 6,
                "offset": 2
            }
        },
        "bannerText": "...",
        "autoCollapse": false,
        "kind": "code"
    },
    {
        "textSpan": {
            "start": {
                "line": 5,
                "offset": 10
            },
            "end": {
                "line": 5,
                "offset": 20
            }
        },
        "hintSpan": {
            "start": {
                "line": 5,
                "offset": 10
            },
            "end": {
                "line": 5,
                "offset": 20
            }
        },
        "bannerText": "<>...</>",
        "autoCollapse": false,
        "kind": "code"
    }
]
[Trace  - 23:39:50] <semantic> Sending request: getApplicableRefactors (128). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "startLine": 4,
    "startOffset": 12,
    "endLine": 4,
    "endOffset": 12
}
[Trace  - 23:39:50] <semantic> Response received: getApplicableRefactors (128). Request took 1 ms. Success: true
Result: []
[Trace  - 23:39:50] <semantic> Sending request: geterr (129). Response expected: yes. Current queue length: 0
Arguments: {
    "delay": 0,
    "files": [
        "/Users/Valeriy/Projects/autoimport/pages/index.tsx"
    ]
}
[Trace  - 23:39:50] <semantic> Event received: syntaxDiag (0).
Data: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "diagnostics": []
}
[Trace  - 23:39:50] <semantic> Event received: semanticDiag (0).
Data: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "diagnostics": [
        {
            "start": {
                "line": 3,
                "offset": 16
            },
            "end": {
                "line": 3,
                "offset": 20
            },
            "text": "Cannot find name 'memo'.",
            "code": 2304,
            "category": "error"
        }
    ]
}
[Trace  - 23:39:50] <semantic> Event received: suggestionDiag (0).
Data: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "diagnostics": []
}
[Trace  - 23:39:50] <semantic> Async response received: requestCompleted (129). Request took 4 ms.
[Trace  - 23:39:51] <semantic> Sending request: quickinfo (130). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "line": 4,
    "offset": 12
}
[Trace  - 23:39:51] <semantic> Response received: quickinfo (130). Request took 13 ms. Success: false . Message: No content available.
[Trace  - 23:39:52] <semantic> Sending request: updateOpen (131). Response expected: yes. Current queue length: 0
Arguments: {
    "changedFiles": [
        {
            "fileName": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
            "textChanges": [
                {
                    "newText": "// ",
                    "start": {
                        "line": 4,
                        "offset": 3
                    },
                    "end": {
                        "line": 4,
                        "offset": 3
                    }
                }
            ]
        }
    ],
    "closedFiles": [],
    "openFiles": []
}
[Trace  - 23:39:52] <syntax> Sending request: updateOpen (63). Response expected: yes. Current queue length: 0
Arguments: {
    "changedFiles": [
        {
            "fileName": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
            "textChanges": [
                {
                    "newText": "// ",
                    "start": {
                        "line": 4,
                        "offset": 3
                    },
                    "end": {
                        "line": 4,
                        "offset": 3
                    }
                }
            ]
        }
    ],
    "closedFiles": [],
    "openFiles": []
}
[Trace  - 23:39:52] <semantic> Response received: updateOpen (131). Request took 3 ms. Success: true
Result: true
[Trace  - 23:39:52] <syntax> Response received: updateOpen (63). Request took 4 ms. Success: true
Result: true
[Trace  - 23:39:52] <syntax> Sending request: getOutliningSpans (64). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx"
}
[Trace  - 23:39:52] <syntax> Response received: getOutliningSpans (64). Request took 6 ms. Success: true
Result: [
    {
        "textSpan": {
            "start": {
                "line": 3,
                "offset": 26
            },
            "end": {
                "line": 6,
                "offset": 2
            }
        },
        "hintSpan": {
            "start": {
                "line": 3,
                "offset": 21
            },
            "end": {
                "line": 6,
                "offset": 2
            }
        },
        "bannerText": "...",
        "autoCollapse": false,
        "kind": "code"
    },
    {
        "textSpan": {
            "start": {
                "line": 5,
                "offset": 10
            },
            "end": {
                "line": 5,
                "offset": 20
            }
        },
        "hintSpan": {
            "start": {
                "line": 5,
                "offset": 10
            },
            "end": {
                "line": 5,
                "offset": 20
            }
        },
        "bannerText": "<>...</>",
        "autoCollapse": false,
        "kind": "code"
    }
]
[Trace  - 23:39:52] <semantic> Sending request: getApplicableRefactors (132). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "startLine": 4,
    "startOffset": 15,
    "endLine": 4,
    "endOffset": 15
}
[Trace  - 23:39:52] <syntax> Sending request: navtree (65). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx"
}
[Trace  - 23:39:52] <syntax> Response received: navtree (65). Request took 4 ms. Success: true
Result: {
    "text": "\"index\"",
    "kind": "module",
    "kindModifiers": "",
    "spans": [
        {
            "start": {
                "line": 1,
                "offset": 1
            },
            "end": {
                "line": 6,
                "offset": 5
            }
        }
    ],
    "childItems": [
        {
            "text": "memo() callback",
            "kind": "function",
            "kindModifiers": "",
            "spans": [
                {
                    "start": {
                        "line": 3,
                        "offset": 21
                    },
                    "end": {
                        "line": 6,
                        "offset": 2
                    }
                }
            ]
        },
        {
            "text": "useAmp",
            "kind": "alias",
            "kindModifiers": "",
            "spans": [
                {
                    "start": {
                        "line": 1,
                        "offset": 10
                    },
                    "end": {
                        "line": 1,
                        "offset": 16
                    }
                }
            ],
            "nameSpan": {
                "start": {
                    "line": 1,
                    "offset": 10
                },
                "end": {
                    "line": 1,
                    "offset": 16
                }
            }
        }
    ]
}
[Trace  - 23:39:52] <semantic> Response received: getApplicableRefactors (132). Request took 28 ms. Success: true
Result: []
[Trace  - 23:39:52] <semantic> Sending request: geterr (133). Response expected: yes. Current queue length: 0
Arguments: {
    "delay": 0,
    "files": [
        "/Users/Valeriy/Projects/autoimport/pages/index.tsx"
    ]
}
[Trace  - 23:39:52] <semantic> Event received: syntaxDiag (0).
Data: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "diagnostics": []
}
[Trace  - 23:39:52] <semantic> Event received: semanticDiag (0).
Data: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "diagnostics": [
        {
            "start": {
                "line": 3,
                "offset": 16
            },
            "end": {
                "line": 3,
                "offset": 20
            },
            "text": "Cannot find name 'memo'.",
            "code": 2304,
            "category": "error"
        }
    ]
}
[Trace  - 23:39:52] <semantic> Event received: suggestionDiag (0).
Data: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "diagnostics": [
        {
            "start": {
                "line": 1,
                "offset": 1
            },
            "end": {
                "line": 1,
                "offset": 35
            },
            "text": "'useAmp' is declared but its value is never read.",
            "code": 6133,
            "category": "suggestion",
            "reportsUnnecessary": true
        }
    ]
}
[Trace  - 23:39:52] <semantic> Async response received: requestCompleted (133). Request took 20 ms.
[Trace  - 23:39:52] <semantic> Sending request: getApplicableRefactors (134). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "startLine": 4,
    "startOffset": 15,
    "endLine": 4,
    "endOffset": 15
}
[Trace  - 23:39:52] <semantic> Response received: getApplicableRefactors (134). Request took 2 ms. Success: true
Result: []
[Trace  - 23:39:53] <semantic> Sending request: getApplicableRefactors (135). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "startLine": 1,
    "startOffset": 35,
    "endLine": 1,
    "endOffset": 35
}
[Trace  - 23:39:53] <semantic> Response received: getApplicableRefactors (135). Request took 1 ms. Success: true
Result: []
[Trace  - 23:39:53] <semantic> Sending request: getCodeFixes (136). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "startLine": 1,
    "startOffset": 1,
    "endLine": 1,
    "endOffset": 35,
    "errorCodes": [
        6133
    ]
}
[Trace  - 23:39:53] <semantic> Response received: getCodeFixes (136). Request took 1 ms. Success: true
Result: [
    {
        "fixName": "unusedIdentifier",
        "description": "Remove import from 'next/amp'",
        "changes": [
            {
                "fileName": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
                "textChanges": [
                    {
                        "start": {
                            "line": 1,
                            "offset": 1
                        },
                        "end": {
                            "line": 2,
                            "offset": 1
                        },
                        "newText": ""
                    }
                ]
            }
        ],
        "fixId": "unusedIdentifier_delete",
        "fixAllDescription": "Delete all unused declarations"
    }
]
[Trace  - 23:39:54] <semantic> Sending request: updateOpen (137). Response expected: yes. Current queue length: 0
Arguments: {
    "changedFiles": [
        {
            "fileName": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
            "textChanges": [
                {
                    "newText": "// ",
                    "start": {
                        "line": 1,
                        "offset": 1
                    },
                    "end": {
                        "line": 1,
                        "offset": 1
                    }
                }
            ]
        }
    ],
    "closedFiles": [],
    "openFiles": []
}
[Trace  - 23:39:54] <syntax> Sending request: updateOpen (66). Response expected: yes. Current queue length: 0
Arguments: {
    "changedFiles": [
        {
            "fileName": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
            "textChanges": [
                {
                    "newText": "// ",
                    "start": {
                        "line": 1,
                        "offset": 1
                    },
                    "end": {
                        "line": 1,
                        "offset": 1
                    }
                }
            ]
        }
    ],
    "closedFiles": [],
    "openFiles": []
}
[Trace  - 23:39:54] <semantic> Response received: updateOpen (137). Request took 2 ms. Success: true
Result: true
[Trace  - 23:39:54] <syntax> Response received: updateOpen (66). Request took 1 ms. Success: true
Result: true
[Trace  - 23:39:54] <syntax> Sending request: getOutliningSpans (67). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx"
}
[Trace  - 23:39:54] <syntax> Response received: getOutliningSpans (67). Request took 2 ms. Success: true
Result: [
    {
        "textSpan": {
            "start": {
                "line": 3,
                "offset": 26
            },
            "end": {
                "line": 6,
                "offset": 2
            }
        },
        "hintSpan": {
            "start": {
                "line": 3,
                "offset": 21
            },
            "end": {
                "line": 6,
                "offset": 2
            }
        },
        "bannerText": "...",
        "autoCollapse": false,
        "kind": "code"
    },
    {
        "textSpan": {
            "start": {
                "line": 5,
                "offset": 10
            },
            "end": {
                "line": 5,
                "offset": 20
            }
        },
        "hintSpan": {
            "start": {
                "line": 5,
                "offset": 10
            },
            "end": {
                "line": 5,
                "offset": 20
            }
        },
        "bannerText": "<>...</>",
        "autoCollapse": false,
        "kind": "code"
    }
]
[Trace  - 23:39:54] <semantic> Sending request: getApplicableRefactors (138). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "startLine": 1,
    "startOffset": 38,
    "endLine": 1,
    "endOffset": 38
}
[Trace  - 23:39:54] <syntax> Sending request: navtree (68). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx"
}
[Trace  - 23:39:54] <syntax> Response received: navtree (68). Request took 3 ms. Success: true
Result: {
    "text": "\"index\"",
    "kind": "module",
    "kindModifiers": "",
    "spans": [
        {
            "start": {
                "line": 1,
                "offset": 1
            },
            "end": {
                "line": 6,
                "offset": 5
            }
        }
    ],
    "childItems": [
        {
            "text": "memo() callback",
            "kind": "function",
            "kindModifiers": "",
            "spans": [
                {
                    "start": {
                        "line": 3,
                        "offset": 21
                    },
                    "end": {
                        "line": 6,
                        "offset": 2
                    }
                }
            ]
        }
    ]
}
[Trace  - 23:39:54] <semantic> Response received: getApplicableRefactors (138). Request took 40 ms. Success: true
Result: []
[Trace  - 23:39:54] <semantic> Sending request: geterr (139). Response expected: yes. Current queue length: 0
Arguments: {
    "delay": 0,
    "files": [
        "/Users/Valeriy/Projects/autoimport/pages/index.tsx"
    ]
}
[Trace  - 23:39:54] <semantic> Event received: syntaxDiag (0).
Data: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "diagnostics": []
}
[Trace  - 23:39:54] <semantic> Event received: semanticDiag (0).
Data: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "diagnostics": [
        {
            "start": {
                "line": 3,
                "offset": 16
            },
            "end": {
                "line": 3,
                "offset": 20
            },
            "text": "Cannot find name 'memo'.",
            "code": 2304,
            "category": "error"
        }
    ]
}
[Trace  - 23:39:54] <semantic> Event received: suggestionDiag (0).
Data: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "diagnostics": []
}
[Trace  - 23:39:54] <semantic> Async response received: requestCompleted (139). Request took 13 ms.
[Trace  - 23:39:54] <semantic> Sending request: getApplicableRefactors (140). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "startLine": 1,
    "startOffset": 38,
    "endLine": 1,
    "endOffset": 38
}
[Trace  - 23:39:54] <semantic> Response received: getApplicableRefactors (140). Request took 1 ms. Success: true
Result: []
[Trace  - 23:39:55] <semantic> Sending request: quickinfo (141). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "line": 3,
    "offset": 18
}
[Trace  - 23:39:55] <semantic> Response received: quickinfo (141). Request took 5 ms. Success: true
Result: {
    "kind": "",
    "kindModifiers": "",
    "start": {
        "line": 3,
        "offset": 16
    },
    "end": {
        "line": 3,
        "offset": 20
    },
    "displayString": "any",
    "documentation": "",
    "tags": []
}
[Trace  - 23:39:56] <semantic> Sending request: getCodeFixes (142). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "startLine": 3,
    "startOffset": 16,
    "endLine": 3,
    "endOffset": 20,
    "errorCodes": [
        2304
    ]
}
[Trace  - 23:39:56] <semantic> Response received: getCodeFixes (142). Request took 12 ms. Success: true
Result: [
    {
        "fixName": "import",
        "description": "Import 'memo' from module \"react\"",
        "changes": [
            {
                "fileName": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
                "textChanges": [
                    {
                        "start": {
                            "line": 1,
                            "offset": 1
                        },
                        "end": {
                            "line": 1,
                            "offset": 1
                        },
                        "newText": "import { memo } from \"react\";\n\n"
                    }
                ]
            }
        ],
        "fixId": "fixMissingImport",
        "fixAllDescription": "Add all missing imports"
    }
]
[Trace  - 23:39:57] <semantic> Sending request: quickinfo (143). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "line": 3,
    "offset": 17
}
[Trace  - 23:39:57] <semantic> Response received: quickinfo (143). Request took 1 ms. Success: true
Result: {
    "kind": "",
    "kindModifiers": "",
    "start": {
        "line": 3,
        "offset": 16
    },
    "end": {
        "line": 3,
        "offset": 20
    },
    "displayString": "any",
    "documentation": "",
    "tags": []
}
[Trace  - 23:39:57] <semantic> Sending request: getCodeFixes (144). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "startLine": 3,
    "startOffset": 16,
    "endLine": 3,
    "endOffset": 20,
    "errorCodes": [
        2304
    ]
}
[Trace  - 23:39:57] <semantic> Response received: getCodeFixes (144). Request took 3 ms. Success: true
Result: [
    {
        "fixName": "import",
        "description": "Import 'memo' from module \"react\"",
        "changes": [
            {
                "fileName": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
                "textChanges": [
                    {
                        "start": {
                            "line": 1,
                            "offset": 1
                        },
                        "end": {
                            "line": 1,
                            "offset": 1
                        },
                        "newText": "import { memo } from \"react\";\n\n"
                    }
                ]
            }
        ],
        "fixId": "fixMissingImport",
        "fixAllDescription": "Add all missing imports"
    }
]
[Trace  - 23:39:59] <semantic> Sending request: quickinfo (145). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "line": 3,
    "offset": 17
}
[Trace  - 23:39:59] <semantic> Response received: quickinfo (145). Request took 1 ms. Success: true
Result: {
    "kind": "",
    "kindModifiers": "",
    "start": {
        "line": 3,
        "offset": 16
    },
    "end": {
        "line": 3,
        "offset": 20
    },
    "displayString": "any",
    "documentation": "",
    "tags": []
}
[Trace  - 23:39:59] <semantic> Sending request: quickinfo (146). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "line": 3,
    "offset": 17
}
[Trace  - 23:39:59] <semantic> Response received: quickinfo (146). Request took 2 ms. Success: true
Result: {
    "kind": "",
    "kindModifiers": "",
    "start": {
        "line": 3,
        "offset": 16
    },
    "end": {
        "line": 3,
        "offset": 20
    },
    "displayString": "any",
    "documentation": "",
    "tags": []
}
[Trace  - 23:39:59] <semantic> Sending request: getCodeFixes (147). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "startLine": 3,
    "startOffset": 16,
    "endLine": 3,
    "endOffset": 20,
    "errorCodes": [
        2304
    ]
}
[Trace  - 23:39:59] <semantic> Response received: getCodeFixes (147). Request took 7 ms. Success: true
Result: [
    {
        "fixName": "import",
        "description": "Import 'memo' from module \"react\"",
        "changes": [
            {
                "fileName": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
                "textChanges": [
                    {
                        "start": {
                            "line": 1,
                            "offset": 1
                        },
                        "end": {
                            "line": 1,
                            "offset": 1
                        },
                        "newText": "import { memo } from \"react\";\n\n"
                    }
                ]
            }
        ],
        "fixId": "fixMissingImport",
        "fixAllDescription": "Add all missing imports"
    }
]
[Trace  - 23:40:01] <semantic> Sending request: updateOpen (148). Response expected: yes. Current queue length: 0
Arguments: {
    "changedFiles": [
        {
            "fileName": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
            "textChanges": [
                {
                    "newText": "import { memo } from \"react\";\n\n",
                    "start": {
                        "line": 1,
                        "offset": 1
                    },
                    "end": {
                        "line": 1,
                        "offset": 1
                    }
                }
            ]
        }
    ],
    "closedFiles": [],
    "openFiles": []
}
[Trace  - 23:40:01] <syntax> Sending request: updateOpen (69). Response expected: yes. Current queue length: 0
Arguments: {
    "changedFiles": [
        {
            "fileName": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
            "textChanges": [
                {
                    "newText": "import { memo } from \"react\";\n\n",
                    "start": {
                        "line": 1,
                        "offset": 1
                    },
                    "end": {
                        "line": 1,
                        "offset": 1
                    }
                }
            ]
        }
    ],
    "closedFiles": [],
    "openFiles": []
}
[Trace  - 23:40:01] <semantic> Response received: updateOpen (148). Request took 1 ms. Success: true
Result: true
[Trace  - 23:40:01] <semantic> Sending request: getApplicableRefactors (149). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "startLine": 3,
    "startOffset": 38,
    "endLine": 3,
    "endOffset": 38
}
[Trace  - 23:40:01] <syntax> Response received: updateOpen (69). Request took 1 ms. Success: true
Result: true
[Trace  - 23:40:01] <semantic> Response received: getApplicableRefactors (149). Request took 59 ms. Success: true
Result: []
[Trace  - 23:40:01] <syntax> Sending request: getOutliningSpans (70). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx"
}
[Trace  - 23:40:01] <syntax> Response received: getOutliningSpans (70). Request took 4 ms. Success: true
Result: [
    {
        "textSpan": {
            "start": {
                "line": 5,
                "offset": 26
            },
            "end": {
                "line": 8,
                "offset": 2
            }
        },
        "hintSpan": {
            "start": {
                "line": 5,
                "offset": 21
            },
            "end": {
                "line": 8,
                "offset": 2
            }
        },
        "bannerText": "...",
        "autoCollapse": false,
        "kind": "code"
    },
    {
        "textSpan": {
            "start": {
                "line": 7,
                "offset": 10
            },
            "end": {
                "line": 7,
                "offset": 20
            }
        },
        "hintSpan": {
            "start": {
                "line": 7,
                "offset": 10
            },
            "end": {
                "line": 7,
                "offset": 20
            }
        },
        "bannerText": "<>...</>",
        "autoCollapse": false,
        "kind": "code"
    }
]
[Trace  - 23:40:01] <semantic> Sending request: getApplicableRefactors (150). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "startLine": 3,
    "startOffset": 38,
    "endLine": 3,
    "endOffset": 38
}
[Trace  - 23:40:01] <semantic> Response received: getApplicableRefactors (150). Request took 2 ms. Success: true
Result: []
[Trace  - 23:40:01] <syntax> Sending request: navtree (71). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx"
}
[Trace  - 23:40:01] <syntax> Response received: navtree (71). Request took 1 ms. Success: true
Result: {
    "text": "\"index\"",
    "kind": "module",
    "kindModifiers": "",
    "spans": [
        {
            "start": {
                "line": 1,
                "offset": 1
            },
            "end": {
                "line": 8,
                "offset": 5
            }
        }
    ],
    "childItems": [
        {
            "text": "memo",
            "kind": "alias",
            "kindModifiers": "",
            "spans": [
                {
                    "start": {
                        "line": 1,
                        "offset": 10
                    },
                    "end": {
                        "line": 1,
                        "offset": 14
                    }
                }
            ],
            "nameSpan": {
                "start": {
                    "line": 1,
                    "offset": 10
                },
                "end": {
                    "line": 1,
                    "offset": 14
                }
            }
        },
        {
            "text": "memo() callback",
            "kind": "function",
            "kindModifiers": "",
            "spans": [
                {
                    "start": {
                        "line": 5,
                        "offset": 21
                    },
                    "end": {
                        "line": 8,
                        "offset": 2
                    }
                }
            ]
        }
    ]
}
[Trace  - 23:40:02] <semantic> Sending request: geterr (151). Response expected: yes. Current queue length: 0
Arguments: {
    "delay": 0,
    "files": [
        "/Users/Valeriy/Projects/autoimport/pages/index.tsx"
    ]
}
[Trace  - 23:40:02] <semantic> Event received: syntaxDiag (0).
Data: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "diagnostics": []
}
[Trace  - 23:40:02] <semantic> Event received: semanticDiag (0).
Data: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "diagnostics": []
}
[Trace  - 23:40:02] <semantic> Event received: suggestionDiag (0).
Data: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "diagnostics": []
}
[Trace  - 23:40:02] <semantic> Async response received: requestCompleted (151). Request took 24 ms.
[Trace  - 23:40:02] <semantic> Sending request: getApplicableRefactors (152). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "startLine": 3,
    "startOffset": 38,
    "endLine": 3,
    "endOffset": 38
}
[Trace  - 23:40:02] <semantic> Response received: getApplicableRefactors (152). Request took 1 ms. Success: true
Result: []
[Trace  - 23:49:20] <semantic> Sending request: documentHighlights (153). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "line": 1,
    "offset": 3,
    "filesToSearch": [
        "/Users/Valeriy/Projects/autoimport/pages/index.tsx"
    ]
}
[Trace  - 23:49:20] <semantic> Response received: documentHighlights (153). Request took 33 ms. Success: true
Result: []
[Trace  - 23:49:20] <semantic> Sending request: getApplicableRefactors (154). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "startLine": 1,
    "startOffset": 1,
    "endLine": 1,
    "endOffset": 30
}
[Trace  - 23:49:20] <semantic> Response received: getApplicableRefactors (154). Request took 27 ms. Success: true
Result: [
    {
        "name": "Convert import",
        "description": "Convert named imports to namespace import",
        "actions": [
            {
                "name": "Convert named imports to namespace import",
                "description": "Convert named imports to namespace import"
            }
        ]
    }
]
[Trace  - 23:49:21] <semantic> Sending request: getApplicableRefactors (155). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "startLine": 1,
    "startOffset": 30,
    "endLine": 1,
    "endOffset": 30
}
[Trace  - 23:49:21] <semantic> Response received: getApplicableRefactors (155). Request took 1 ms. Success: true
Result: []
[Trace  - 23:49:21] <semantic> Sending request: documentHighlights (156). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "line": 3,
    "offset": 7,
    "filesToSearch": [
        "/Users/Valeriy/Projects/autoimport/pages/index.tsx"
    ]
}
[Trace  - 23:49:21] <semantic> Response received: documentHighlights (156). Request took 1 ms. Success: true
Result: []
[Trace  - 23:49:22] <semantic> Sending request: getApplicableRefactors (157). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "startLine": 3,
    "startOffset": 4,
    "endLine": 3,
    "endOffset": 38
}
[Trace  - 23:49:22] <semantic> Response received: getApplicableRefactors (157). Request took 1 ms. Success: true
Result: []
[Trace  - 23:49:22] <semantic> Sending request: quickinfo (158). Response expected: yes. Current queue length: 0
Arguments: {
    "file": "/Users/Valeriy/Projects/autoimport/pages/index.tsx",
    "line": 3,
    "offset": 38
}
[Trace  - 23:49:22] <semantic> TypeScript Server: trying to cancel ongoing request with sequence number 158

```
