# Get_max_value_by_remove_one_char_in_number
Get max value by remove one char in number



      function getMax(N, L, K) {
          var arr = N.toString().split('').map(Number);
          var count = 0, index = 0;
          var newN = [];
          var n = arr[0];
          var need = L - K;
          var flag = false;

          while (count < need) {
              for (var i = index; i < arr.length; i++) {
                  if (n < arr[i] && arr.length - i >= need - count) {

                      for (var j = 0; j < newN.length; j++) {
                          if (newN[j].index === i) {
                              flag = true;
                              break;
                          }
                      }

                      if (flag === false) {
                          n = arr[i];
                          index = i;
                      }
                      flag = false;
                  }
              }
              newN.push({value: n, index: index});
              n = -1;
              count++;
          }

          newN.sort(function (a, b) {
              var c = a.index;
              var d = b.index;
              return c - d;
          });

          var string = '';
          for (var i = 0; i < newN.length; i++) {
              string += newN[i].value.toString();
          }
          return parseInt(string);
      }
